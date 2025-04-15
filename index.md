---
layout: default
title: Home
---

# My Blog Posts

<div class="post-list">
  {% for post in site.posts %}
    <article class="home-post">
      <h2>{{ post.title }}</h2>
      <p><em>{{ post.date | date: "%Y-%m-%d" }}</em></p>
      {{ post.content }}
      <hr>
    </article>
  {% endfor %}
</div>
