---
layout: page
title: "Weekly Blog"
---

Welcome to the project development blog!  
Click a week below to read that update.

{% for post in site.posts %}
  <a href="{{ post.url }}">{{ post.title }}</a><br>
{% endfor %}