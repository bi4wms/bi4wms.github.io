---
title: Blog
layout: page
permalink: /blog/
icon: fas fa-newspaper
order: 6
---

<style>
/* 与首页卡片完全一致的核心样式 */
.card-title,
.card-title a {
    font-size: 1.25rem !important;
    line-height: 1.35 !important;
    margin-top: 0.25rem !important;
    margin-bottom: 0.65rem !important;
    color: var(--link-color) !important;           /* 关键：跟随主题链接色 */
    text-decoration: none !important;
}

.card-title a:hover {
    color: var(--link-hover-color) !important;
}

/* 阅读全文 - 与首页一致 */
.read-more {
    color: var(--link-color) !important;
    font-weight: 500;
    text-decoration: none !important;
}

.read-more:hover {
    color: var(--link-hover-color) !important;
}

/* 日期 - 恢复跟随 Dark Mode */
.post-meta,
.post-meta time {
    color: var(--text-muted) !important;
    font-size: 0.9rem !important;
}

/* 卡片基础（保持稳定） */
.post-list .card {
    background-color: var(--card-bg) !important;
    border: 1px solid var(--border-color) !important;
    box-shadow: var(--card-shadow) !important;
    margin-top: 0 !important;
}

.post-list {
    gap: 1.55rem !important;
}

/* 缩略文 */
.card-text {
    color: var(--text-color) !important;
    font-size: 0.95rem !important;
    margin-bottom: 0.85rem !important;
}
</style>

{% assign blog_posts = site.posts | where_exp: "post", "post.categories contains 'Blog'" | sort: "date" | reverse %}

<div class="post-list" style="display: flex; flex-direction: column; gap: 1.55rem;">
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
