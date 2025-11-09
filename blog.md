---
layout: page
title: "Weekly Blog"
---

Welcome to the project development blog!  
Click a week below to read that update.

<ul>
  {% for post in site.posts %}
    <li><a href="{{ post.url | relative_url }}">{{ post.title }}</a></li>
  {% endfor %}
</ul>