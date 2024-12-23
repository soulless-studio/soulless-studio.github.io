---
layout: page
title: Blog
permalink: /blog/
---

<div class="blog-list">
  {% for post in site.posts %}
    <article class="blog-post">
      <h2>
        <a class="blog-title" href="{{ post.url | relative_url }}">{{ post.title }}</a>
      </h2>
      <div class="blog-meta">
        {{ post.date | date: "%B %-d, %Y" }}
      </div>
      {% if post.excerpt %}
        {{ post.excerpt }}
        <a href="{{ post.url | relative_url }}">Read more...</a>
      {% endif %}
    </article>
  {% endfor %}
</div>
