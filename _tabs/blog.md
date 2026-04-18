---
title: Blog
layout: page
permalink: /blog/
icon: fas fa-newspaper
order: 6
---

<style>
/* 参照 Chirpy 官方首页卡片风格 + 完整 Dark Mode 支持 */
.card-title,
.card-title a {
    font-size: 1.25rem !important;
    line-height: 1.35 !important;
    margin-top: 0.25rem !important;
    margin-bottom: 0.65rem !important;
    color: var(--link-color) !important;        /* 标题链接跟随主题颜色 */
}

.card-title a:hover {
    color: var(--link-hover-color) !important;  /* hover 时更明显 */
}

.card-body {
    padding: 1.35rem 1.4rem !important;
}

/* 卡片整体样式 */
.post-list {
    gap: 1.55rem !important;
}

.post-list .card {
    margin-top: 0 !important;
    background-color: var(--card-bg) !important;
    border: 1px solid var(--border-color) !important;
    box-shadow: var(--card-shadow) !important;
    transition: all 0.2s ease;
}

.post-list .card:hover {
    transform: translateY(-3px);
    box-shadow: 0 8px 25px rgba(0, 0, 0, 0.15) !important;
}

/* 缩略文（excerpt） - 已修复 Dark Mode 可见性 */
.card-text {
    color: var(--text-color) !important;
    margin-bottom: 0.85rem !important;
    font-size: 0.95rem !important;
}

/* 日期 - 强制跟随 Dark Mode（首页标准方式） */
.post-meta,
.post-meta time {
    color: var(--text-muted) !important;
    font-size: 0.9rem;
}

/* 阅读全文链接 - 跟随系统调整 */
.read-more {
    color: var(--link-color) !important;
    font-weight: 500;
}

.read-more:hover {
    color: var(--link-hover-color) !important;
    text-decoration: underline;
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
