---
layout: default
title: Home
---

# My Blog Posts

<ul>
  {% for post in site.posts %}
    <li>
      <h2><a href="{{ post.url }}">{{ post.title }}</a></h2>
      <p>{{ post.excerpt }}</p>
      <p><small>{{ post.date | date: "%Y-%m-%d" }}</small></p>
    </li>
  {% endfor %}
</ul>
