---
layout: archive
permalink: categories/coding/
author_profile: true
---
<img src="https://github.com/INMD1/blog-site/blob/main/assets/image/codeing.jpg?raw=true" 
style=" width: 100vw; height: 30vh; 
        object-fit: cover;
        ">
<h2>현재 우리가 하면서 알아낸 지식을 적는곳</h2>
<hr>
{% assign posts = site.categories.coding %}
{% for post in posts %} {% include archive-single.html type=page.entries_layout %} {% endfor %}