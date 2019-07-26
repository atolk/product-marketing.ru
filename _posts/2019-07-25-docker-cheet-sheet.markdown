---
layout: post
comments: true
title:  "Docker - PM's R&D"
date:   2019-07-25 09:00:00 +0300
categories: [tools]
tags: [docker, linux]
---

В своей ежедневной работе мне приходится использовать/тестировать/изучать большое количество ПО. Docker для меня - это уже не просто ПО, а платформенная часть рабочего окружения в одном ряду с Chrome и VS Code.

Docker - это виртуальные машины на стероидах. Скачиваете себе образ (image) -> запускаете образ в контейнере (container) в изолированном окружении. Эта концепция идеально ложится в объектно-ориентированную парадигму программирования: класс -> экземпляр класса.

Образы (images) - это уже сконфигурированное ПО (со своей ОС). Они неизменяемые. Вы запускаете образ - создается контейнер. Можно запустить неограниченное количество контейнеров одного образа.

Зачем? Вот [здесь](https://toster.ru/q/321203){:title="toster.ru" target="_blank"} доступно написано. Для меня это в первую очередь безопасная песочница для экспериментов. Так я защищен от dll hell (ок, в linux [dependecy hell](https://ru.wikipedia.org/wiki/Dependency_hell){: target="_blank"}) и забыл, что такое деградирование ОС.

Вся инфраструктура состоит из двух частей:
* [DockerHub](https://hub.docker.com/){: target="_blank"} - глобальное хранилище образов. github контейнеризации;
* ПО на вашем компе, управляемое через командную строку (CLI).

Устанавливаем Docker в linux:
{% highlight bash %}
$ curl -fsSL https://get.docker.com -o get-docker.sh
$ sudo sh get-docker.sh
$ sudo usermod -aG docker $(whoami)
{% endhighlight %}

[Читаем инструкцию](https://docs.docker.com/docker-for-windows/install/){: target="_blank"}, качаем и устанавливаем в Windows.

Проверяем, что все работает:
{% highlight bash %}
$ docker run hello-world
Hello from Docker!
This message shows that your installation appears to be working correctly.
...
{% endhighlight %}

Вуаля! Ваша ОС защищена от деградации из-за зоппарка тулзов и готова к любым экспериментам с ПО с любой интенсивностью, а вы сами теперь принадлежите к касте избранных, стоящих на передовой технологий. Кому что важнее.


## Кейс использования Docker у меня такой:

1. Где-то узнал про потенциально полезное ПО.
2. Лезу на [DockerHub](https://hub.docker.com/){: target="_blank"} искать образ.
3. Скачиваю себе образ. 
4. Конфигурирую контейнер и работаю с ним.
5. 1-4 повторить n раз.
6. В какой-то момент (скорее по зову сердца, чем по необходимости) делаю clean up.

## Самые часто используемые CLI-команды

Для примера возьмем что-нибудь поинтереснее hello-world. [Jupyter notebook](https://jupyter.org/){: target="_blank"} с python на борту: [jupyter/scipy-notebook](https://hub.docker.com/r/jupyter/scipy-notebook){: target="_blank"} - джентельменский набор аналитика.

### Скачивание образа из DockerHub:
{% highlight bash %}
# общий вид
docker pull publisher/image
# конретный образ
docker pull jupyter/scipy-notebook
{% endhighlight %}

### Создание и запуск контейнера из образа. 
Если образ не будет найден, то docker автоматически сделает `pull` из DockerHub, так что можно обойтись и без предыдущей команды.
{% highlight bash %}
# общий вид
docker run publisher/image
# конретный образ
docker run jupyter/scipy-notebook
{% endhighlight %}

Остановить таким образом запущенный контейнер можно с помощью ctrl+c.

Из документации к контейнеру ([здесь](https://jupyter-docker-stacks.readthedocs.io/en/latest/index.html){: target="_blank"}) мы знаем, что контейнер пробрасывает (exposes) наружу порт 8888. Эту же информацию можно увидеть в командной строке среди логов запуска контейнера. Но Docker сам по себе порт на хост не пробрасывает. Укажем ему на это:

### Пробрасывание портов
{% highlight bash %}
# общий вид
docker run -p hhhh:cccc publisher/image
# h - host port, c - container port

# конркетный образ
docker run -p 1000:8888 jupyter/scipy-notebook
{% endhighlight %}

Открываем браузер, заходим на `http://localhost:1000` и видим приглашение jupyter! Можно в консоли отыскать токен, ввести его в поле и начать работать. Только результаты работы не будут сохраняться.

### Подключение к контейнеру локальной директории
Конретную директорию, содержание которой необходимо сохранять между запусками контейнера, нужно уточнять в документации образа.

{% highlight bash %}
# общий вид
docker run --mount type=bind,source=/host/folder/path,taget=/container/folder/path publisher/image

# все вместе 
docker run -p 1000:8888 --mount type=bind,source=/home/atolk/Sources/notebooks,target=/home/joyvan/work jupyter/scipy-notebook
{% endhighlight %}

Каждый раз, когда вы будете запускать `docker run publisher/image`, docker будет создавать **новый** контейнер из образа. При этом старый не будет уничтожаться.
Как же не плодить контейнеры?

### Именованные контейнеры
Когда вы создаете контейнер, докер присваивает ему случайное имя ([и они прикольные](https://frightanic.com/computers/docker-default-container-names/){: target="_blank"}). Но мы можем задать свое.

{% highlight bash %}
# общий вид
docker run --name my_container_name publisher/image
# и все вместе
docker run -p 1000:8888 --name py-notebook --mount type=bind,source=/home/atolk/Sources/notebooks,target=/home/joyvan/work jupyter/scipy-notebook
{% endhighlight %}

Теперь у вас есть сконфигурированный контейнер, и можно всегда запусктать и останавливать именно его.
{% highlight bash %}
# общий вид
docker start my_container_name
# или 
docker start -i my_container_name
# остановить
docker stop my_container_name

# и все вместе
docker start py-notebook
docker start -i py-notebook
docker stop py-notebook
{% endhighlight %}

Контейнер по умолчанию запускается в бэкграунде и ничего привычного не выводит в консоль. Второй вариант с аргументом `-i` от слова interactive как раз подключает нашу консоль к контейнеру.

### Администрирование (уборка)

{% highlight bash %}

# Все мои скачанные образы
docker images
# Удалить все образы
docker rmi $(docker images -a -q)

# Все созданные контейнеры
docker container ls --all
# Удалить все созданные контейнеры
docker container rm $(docker container ls -all -q)

# удалить неиспользуемое
docker system prune
{% endhighlight %}

Всем крутых экспериментов! )
