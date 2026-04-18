---
title: Blog
layout: page
permalink: /blog/
icon: fas fa-newspaper
order: 6
---

<style>
/* 最高优先级强制覆盖标题和阅读全文颜色（跟随主题） */
.post-list .card-title a,
.post-list .card .card-title a,
.card-title a {
    color: var(--link-color) !important;
    text-decoration: none !important;
}

.post-list .card-title a:hover,
.card-title a:hover {
    color: var(--link-hover-color) !important;
    text-decoration: underline !important;
}

.post-list .read-more,
.read-more {
    color: var(--link-color) !important;
    text-decoration: none !important;
}

.post-list .read-more:hover,
.read-more:hover {
    color: var(--link-hover-color) !important;
}

/* 日期跟随模式 */
.post-meta time {
    color: var(--text-muted) !important;
}
</style>

{% assign blog_posts = site.posts | where_exp: "post", "post.categories contains 'Blog'" | sort: "date" | reverse %}

<div class="post-list">
  {% for post in blog_posts %}
    <article class="card">
      <div class="card-body">
        <h2 class="card-title">
          <a href="{{ post.url | relative_url }}">{{ post.title }}</a>
        </h2>

        {% if post.description %}
          <p class="card-text">{{ post.description }}</p>
        {% elsif post.excerpt %}
          <p class="card-text">{{ post.excerpt | strip_html | truncate: 180 }}</p>
        {% endif %}

        <div class="post-meta">
          <time datetime="{{ post.date | date_to_xmlschema }}">{{ post.date | date: "%Y-%m-%d" }}</time>
        </div>

        <a href="{{ post.url | relative_url }}" class="read-more">阅读全文 →</a>
      </div>
    </article>
  {% endfor %}
</div>

{% if blog_posts.size == 0 %}
  <p class="text-center py-5">暂无 Blog 文章</p>
{% endif %}
