---
layout: default
title: Blog
permalink: /blog/
---

# Blog

<ul class="post-list">
  {% for post in site.posts %}
    <li class="post-item">
      <div class="post-item-title">
        <a href="{{ post.url | relative_url }}">{{ post.title }}</a>
      </div>

      <div class="post-item-meta">
        <span class="post-date">{{ post.date | date: "%Y-%m-%d" }}</span>
        {% if post.tags and post.tags.size > 0 %}
          <span class="post-tags">
            {% for tag in post.tags %}
              {% assign tag_slug = tag | slugify %}
              <a class="tag" href="{{ '/tag/' | append: tag_slug | append: '/' | relative_url }}">#{{ tag }}</a>{% unless forloop.last %} {% endunless %}
            {% endfor %}
          </span>
        {% endif %}
      </div>

      <div class="post-item-excerpt">
        {{ post.excerpt }}
      </div>

      <div class="post-item-more">
        <a href="{{ post.url | relative_url }}">Read more</a>
      </div>
    </li>
  {% endfor %}
</ul>
