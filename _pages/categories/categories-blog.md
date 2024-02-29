---
layout: archive
permalink: categories/blog/
author_profile: true
---
<img src="https://github.com/INMD1/blog-site/blob/main/assets/image/blog1.jpg?raw=true" 
style=" width: 100vw; height: 30vh; 
        object-fit: cover;
        ">
<h2>동아리의 사소한 기록을 남기는곳</h2>
<hr>
{% assign posts = site.categories.blog %}
{% for post in posts %} {% include archive-single.html type=page.entries_layout %} {% endfor %}