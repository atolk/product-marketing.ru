---
layout: page
title: Обо мне
permalink: /about/
---

# Записки продакта

Пишу заметки про продуктовые задачи, с которыми сталкивался [во время работы над проектами](/swiss-army-man.html).

<p>
    <span style="display: inline-block; width:24px;">
        <svg width="24px;" height="24px" fill="#458" display="inline"  version="1.1" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" xml:space="preserve" xmlns:serif="http://www.serif.com/" style="fill-rule:evenodd;clip-rule:evenodd;stroke-linejoin:round;stroke-miterlimit:1.41421;">
            <path id="telegram-2" d="M24,24l-24,0l0,-24l24,0l0,24Zm-7.744,-5.148c0.215,0.153 0.491,0.191 0.738,0.097c0.246,-0.093 0.428,-0.304 0.483,-0.56c0.579,-2.722 1.985,-9.614 2.512,-12.09c0.039,-0.187 -0.027,-0.381 -0.173,-0.506c-0.147,-0.124 -0.351,-0.16 -0.532,-0.093c-2.795,1.034 -11.404,4.264 -14.923,5.567c-0.223,0.082 -0.368,0.297 -0.361,0.533c0.008,0.235 0.167,0.44 0.395,0.509c1.578,0.471 3.65,1.128 3.65,1.128c0,0 0.967,2.924 1.472,4.41c0.063,0.187 0.21,0.334 0.402,0.384c0.193,0.05 0.397,-0.002 0.541,-0.138c0.811,-0.765 2.064,-1.948 2.064,-1.948c0,0 2.381,1.746 3.732,2.707Zm-7.34,-5.784l1.119,3.692l0.249,-2.338c0,0 4.324,-3.9 6.79,-6.124c0.072,-0.065 0.082,-0.174 0.022,-0.251c-0.06,-0.077 -0.169,-0.095 -0.251,-0.043c-2.857,1.825 -7.929,5.064 -7.929,5.064Z"/>
        </svg>
    </span>
    <a href="https://t.me/ProductManager_workdays">
        <span style="display: inline-block; height:100%">Будни продуктов в телеге</span>
    </a>
</p>

Контакты:
<ul class="social-media-list">
    {%- if site.telegram_username -%}
    <li>
      <a href="https://t.me/{{ site.telegram_username }}">
        <svg class="svg-icon" version="1.1" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" xml:space="preserve" xmlns:serif="http://www.serif.com/" style="fill-rule:evenodd;clip-rule:evenodd;stroke-linejoin:round;stroke-miterlimit:1.41421;"><path id="telegram-2" d="M24,24l-24,0l0,-24l24,0l0,24Zm-7.744,-5.148c0.215,0.153 0.491,0.191 0.738,0.097c0.246,-0.093 0.428,-0.304 0.483,-0.56c0.579,-2.722 1.985,-9.614 2.512,-12.09c0.039,-0.187 -0.027,-0.381 -0.173,-0.506c-0.147,-0.124 -0.351,-0.16 -0.532,-0.093c-2.795,1.034 -11.404,4.264 -14.923,5.567c-0.223,0.082 -0.368,0.297 -0.361,0.533c0.008,0.235 0.167,0.44 0.395,0.509c1.578,0.471 3.65,1.128 3.65,1.128c0,0 0.967,2.924 1.472,4.41c0.063,0.187 0.21,0.334 0.402,0.384c0.193,0.05 0.397,-0.002 0.541,-0.138c0.811,-0.765 2.064,-1.948 2.064,-1.948c0,0 2.381,1.746 3.732,2.707Zm-7.34,-5.784l1.119,3.692l0.249,-2.338c0,0 4.324,-3.9 6.79,-6.124c0.072,-0.065 0.082,-0.174 0.022,-0.251c-0.06,-0.077 -0.169,-0.095 -0.251,-0.043c-2.857,1.825 -7.929,5.064 -7.929,5.064Z"/></svg>
        <span>{{ site.telegram_username | escape }}</span>
      </a>
    </li>
  {%- endif -%}


  {%- if site.dribbble_username -%}<li><a href="https://dribbble.com/{{ site.dribbble_username| cgi_escape | escape }}"><svg class="svg-icon"><use xlink:href="{{ '/assets/minima-social-icons.svg#dribbble' | relative_url }}"></use></svg> <span class="username">{{ site.dribbble_username| escape }}</span></a></li>{%- endif -%}
  {%- if site.facebook_username -%}<li><a href="https://www.facebook.com/{{ site.facebook_username| cgi_escape | escape }}"><svg class="svg-icon"><use xlink:href="{{ '/assets/minima-social-icons.svg#facebook' | relative_url }}"></use></svg> <span class="username">{{ site.facebook_username| escape }}</span></a></li>{%- endif -%}
  {%- if site.flickr_username -%}<li><a href="https://www.flickr.com/photos/{{ site.flickr_username| cgi_escape | escape }}"><svg class="svg-icon"><use xlink:href="{{ '/assets/minima-social-icons.svg#flickr' | relative_url }}"></use></svg> <span class="username">{{ site.flickr_username| escape }}</span></a></li>{%- endif -%}
  {%- if site.github_username -%}<li><a href="https://github.com/{{ site.github_username| cgi_escape | escape }}"><svg class="svg-icon"><use xlink:href="{{ '/assets/minima-social-icons.svg#github' | relative_url }}"></use></svg> <span class="username">{{ site.github_username| escape }}</span></a></li>{%- endif -%}
  {%- if site.instagram_username -%}<li><a href="https://instagram.com/{{ site.instagram_username| cgi_escape | escape }}"><svg class="svg-icon"><use xlink:href="{{ '/assets/minima-social-icons.svg#instagram' | relative_url }}"></use></svg> <span class="username">{{ site.instagram_username| escape }}</span></a></li>{%- endif -%}
  {%- if site.linkedin_username -%}<li><a href="https://www.linkedin.com/in/{{ site.linkedin_username| cgi_escape | escape }}"><svg class="svg-icon"><use xlink:href="{{ '/assets/minima-social-icons.svg#linkedin' | relative_url }}"></use></svg> <span class="username">{{ site.linkedin_username| escape }}</span></a></li>{%- endif -%}
  {%- if site.pinterest_username -%}<li><a href="https://www.pinterest.com/{{ site.pinterest_username| cgi_escape | escape }}"><svg class="svg-icon"><use xlink:href="{{ '/assets/minima-social-icons.svg#pinterest' | relative_url }}"></use></svg> <span class="username">{{ site.pinterest_username| escape }}</span></a></li>{%- endif -%}
  {%- for mst in site.mastodon -%}{%- if mst.username and mst.instance -%}<li><a href="https://{{ mst.instance| cgi_escape | escape}}/@{{mst.username}}"><svg class="svg-icon"><use xlink:href="{{ '/assets/minima-social-icons.svg#mastodon' | relative_url }}"></use></svg> <span class="username">{{ mst.username|escape }}</span></a></li>{%- endif -%}{%- endfor -%}
  {%- if site.twitter_username -%}<li><a href="https://www.twitter.com/{{ site.twitter_username| cgi_escape | escape }}"><svg class="svg-icon"><use xlink:href="{{ '/assets/minima-social-icons.svg#twitter' | relative_url }}"></use></svg> <span class="username">{{ site.twitter_username| escape }}</span></a></li>{%- endif -%}
  {%- if site.youtube_username -%}<li><a href="https://youtube.com/{{ site.youtube_username| cgi_escape | escape }}"><svg class="svg-icon"><use xlink:href="{{ '/assets/minima-social-icons.svg#youtube' | relative_url }}"></use></svg> <span class="username">{{ site.youtube_username| escape }}</span></a></li>{%- endif -%}
  {%- if site.googleplus_username -%}<li><a href="https://plus.google.com/{{ site.googleplus_username| escape }}"><svg class="svg-icon"><use xlink:href="{{ '/assets/minima-social-icons.svg#googleplus' | relative_url }}"></use></svg> <span class="username">{{ site.googleplus_username| escape }}</span></a></li>{%- endif -%}
  {%- if site.rss -%}<li><a href="{{ 'feed.xml' | relative_url }}"><svg class="svg-icon"><use xlink:href="{{ '/assets/minima-social-icons.svg#rss' | relative_url }}"></use></svg> <span>{{ site.rss | escape }}</span></a></li>{%- endif -%}
</ul>