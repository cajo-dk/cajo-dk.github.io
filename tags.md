---
layout: default
title: Tags
permalink: /tags/
---

# Tags

<ul class="tag-cloud">
  {% assign all_tags = site.posts | map: "tags" | compact | uniq %}
  {% assign flattened = "" | split: "" %}
  {% for t in all_tags %}
    {% for tag in t %}
      {% assign flattened = flattened | push: tag %}
    {% endfor %}
  {% endfor %}

  {% assign tag_names = flattened | uniq | sort %}

  {% for tag in tag_names %}
    <li>
      <a class="tag" href="{{ '/tag/' | append: tag | slugify | append: '/' | relative_url }}">#{{ tag }}</a>
    </li>
  {% endfor %}
</ul>
