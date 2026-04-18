---
title: Blog
layout: page
permalink: /blog/
fas fa-newspaper
order: 2
---

<h1 class="page-title">{{ page.title }}</h1>

{% assign blog_posts = site.posts | where_exp: "post", "post.categories contains 'Blog'" | sort: "date" | reverse %}

<div id="post-list" class="post-list">
  {% for post in blog_posts %}
    <article class="card">
      <div class="card-body">
        <h2 class="card-title">
          <a href="{{ post.url | relative_url }}">{{ post.title }}</a>
        </h2>

        {% if post.description %}
          <p class="card-text content">{{ post.description }}</p>
        {% elsif post.excerpt %}
          <p class="card-text content">{{ post.excerpt | strip_html | truncate: 200 }}</p>
        {% endif %}

        <div class="post-meta">
          <time datetime="{{ post.date | date_to_xmlschema }}">{{ post.date | date: "%Y-%m-%d" }}</time>
          
          {% if post.tags.size > 0 %}
            • 
            {% for tag in post.tags limit: 3 %}
              <a href="{{ '/tags/' | append: tag | relative_url }}" class="tag">#{{ tag }}</a>
            {% endfor %}
          {% endif %}
        </div>

        <a href="{{ post.url | relative_url }}" class="read-more">阅读全文 →</a>
      </div>
    </article>
  {% endfor %}
</div>

{% if blog_posts.size == 0 %}
  <p>暂无 Blog 文章</p>
{% endif %}
