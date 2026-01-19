---
layout: default
title: Home
---

# Greetings!

I'm an IT architect by day and an incurable tinkerer by night. I spend my working hours thinking about structure, scale, and how technology can actually make life easier for people -- and my late evenings, when the family sleeps, experimenting with whatever caught my curiosity that week.

Most of the projects you'll find here are the result of exactly that: late-night tinkering, half-finished ideas that turned into something useful, and "what if I just try this" moments. Sometimes it's automation, sometimes cloud or AI experiments, sometimes just scratching a technical itch.

I enjoy learning by building, breaking things (preferably in non-production environments), and sharing what I end up with along the way. If something here helps you, sparks an idea, or saves you a bit of time -- mission accomplished.

---

## Recent posts

<ul class="post-list">
  {% for post in site.posts limit: 5 %}
    <li class="post-item">
      <div class="post-item-title">
        <a href="{{ post.url | relative_url }}">{{ post.title }}</a>
      </div>
      <div class="post-item-meta">
        <span class="post-date">{{ post.date | date: "%Y-%m-%d" }}</span>
        {% if post.tags and post.tags.size > 0 %}
          <span class="post-tags">
            {% for tag in post.tags %}
              <a class="tag" href="{{ '/tag/' | append: tag | slugify | append: '/' | relative_url }}">#{{ tag }}</a>{% unless forloop.last %} {% endunless %}
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

<hr class="post-sep" />

<p><a href="{{ '/blog/' | relative_url }}">All posts</a></p>
