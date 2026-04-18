---
title: Guides
layout: page
icon: fas fa-book-open
permalink: /guides/
order: 7
---
{% assign posts = site.posts | where_exp: "post", "post.categories contains 'Guides'" | sort: 'date' | reverse %}<div class="post-list">
  {% for post in posts %}
    <article class="post-preview">
      <h2>
        <a href="{{ post.url | relative_url }}">{{ post.title }}</a>
      </h2>
      
  {% if post.description %}
    <p class="excerpt">{{ post.description }}</p>
  {% elsif post.excerpt %}
    <p class="excerpt">{{ post.excerpt | strip_html | truncate: 200 }}</p>
  {% endif %}

  <div class="post-meta">
    <time datetime="{{ post.date | date_to_xmlschema }}">{{ post.date | date: "%Y-%m-%d" }}</time>
    {% if post.tags.size > 0 %}
      • 
      {% for tag in post.tags %}
        <a href="{{ '/tags/' | append: tag | relative_url }}" class="tag">#{{ tag }}</a>
      {% endfor %}
    {% endif %}
  </div>
  
  <a href="{{ post.url | relative_url }}" class="read-more">阅读全文 →</a>
</article>  {% endfor %}</div>
