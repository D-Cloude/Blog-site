---
layout: archive
permalink: categories/project/
author_profile: true
sidebar_main: true
---
<img src="{{ site.url }}{{ site.baseurl }}/assets/image/projects/mainpage.jpg" 
style=" width: 100vw; height: 30vh;
        object-fit: cover;
        ">
<h2>현재 개발중인 프로젝트를 알리는 곳입니다.</h2>
<p>이 페이지는 유동이 심각하게 많은 곳이기 때문에 포스트가 안올라 올수 있습니다</p>
<hr>
{% assign posts = site.categories.project %}
{% for post in posts %} {% include archive-single.html type=page.entries_layout %} {% endfor %}
