---
layout: default
title: Blog
permalink: /blog/
---

# Blog

<ul class="post-list">
  {% for post in site.posts %}
    <li>
      <span class="post-date">
        {{ post.date | date: "%Y-%m-%d" }}
      </span>
      —
      <a href="{{ post.url | relative_url }}">{{ post.title }}</a>
    </li>
  {% endfor %}
</ul>
