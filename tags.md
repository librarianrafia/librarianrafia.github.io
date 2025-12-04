---
layout: page
title: "Tags"
permalink: /tags/
---

<div class="tags-page">
  <h1>Browse by tag</h1>

  <ul class="tag-cloud">
    {% assign tags = site.tags | sort %}
    {% for tag in tags %}
      {% assign tag_name = tag[0] %}
      {% assign posts = tag[1] %}
      <li>
        <a href="#{{ tag_name | slugify }}">
          {{ tag_name }}
          <span class="tag-count">{{ posts | size }}</span>
        </a>
      </li>
    {% endfor %}
  </ul>

  {% for tag in tags %}
    {% assign tag_name = tag[0] %}
    {% assign posts = tag[1] %}
    <section id="{{ tag_name | slugify }}" class="tag-section">
      <h2>{{ tag_name }}</h2>
      <ul class="tag-post-list">
        {% for post in posts %}
          <li>
            <span class="post-date">{{ post.date | date: "%Y-%m-%d" }}</span>
            <a href="{{ post.url | relative_url }}">{{ post.title }}</a>
          </li>
        {% endfor %}
      </ul>
    </section>
  {% endfor %}
</div>
