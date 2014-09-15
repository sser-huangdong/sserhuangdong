---
layout: page
title: Hello World!
tagline: Supporting tagline
---
{% include JB/setup %}
![首页](/temp_assets/home.jpg)
![test](/temp_assets/10902301.jpg)  

Here's a sample "posts list".

<ul class="posts">
  {% for post in site.posts %}
    <li><span>{{ post.date | date_to_string }}</span> &raquo; <a href="{{ BASE_PATH }}{{ post.url }}">{{ post.title }}</a></li>
  {% endfor %}
</ul>
