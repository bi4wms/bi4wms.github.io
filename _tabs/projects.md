---
title: Projects
layout: page
permalink: /projects/
icon: fas fa-microchip
order: 2
---

<style>
/* ==================== Chirpy 官方卡片风格对齐 + 强力 Dark Mode 支持 ==================== */

/* 标题 - 强制跟随主题链接颜色 */
.card-title,
.card-title a {
    font-size: 1.25rem !important;
    line-height: 1.35 !important;
    margin-top: 0.25rem !important;
    margin-bottom: 0.65rem !important;
    color: var(--link-color) !important;
}

.card-title a:hover {
    color: var(--link-hover-color) !important;
}

/* 卡片基础样式 */
.post-list .card {
    background-color: var(--card-bg) !important;
    border: 1px solid var(--border-color) !important;
    box-shadow: var(--card-shadow) !important;
    margin-top: 0 !important;
    transition: all 0.2s ease;
}

.post-list .card:hover {
    transform: translateY(-3px);
    box-shadow: 0 8px 25px rgba(0,0,0,0.15) !important;
}

/* 缩略文（excerpt） */
.card-text {
    color: var(--text-color) !important;
    font-size: 0.95rem !important;
    margin-bottom: 0.85rem !important;
}

/* 日期 - 加强 Dark Mode */
.post-meta,
.post-meta time {
    color: var(--text-muted) !important;
    font-size: 0.9rem !important;
}

/* 阅读全文 */
.read-more {
    color: var(--link-color) !important;
    font-weight: 500;
}

.read-more:hover {
    color: var(--link-hover-color) !important;
    text-decoration: underline;
}

/* ==================== Dark Mode 专属强制规则（解决没有变化的问题） ==================== */
html[data-mode="dark"] .post-list .card,
html[data-mode="dark"] .card-title a,
html[data-mode="dark"] .card-text,
html[data-mode="dark"] .post-meta,
html[data-mode="dark"] .read-more {
    color: inherit !important;   /* 强制继承主题变量 */
}

/* Dark Mode 下更清晰的文字颜色兜底 */
html[data-mode="dark"] .card-text {
    color: var(--text-color) !important;
}

html[data-mode="dark"] .post-meta,
html[data-mode="dark"] .post-meta time {
    color: var(--text-muted) !important;
}

html[data-mode="dark"] .read-more,
html[data-mode="dark"] .card-title a {
    color: var(--link-color) !important;
}
</style>

{% assign blog_posts = site.posts | where_exp: "post", "post.categories contains 'Projects'" | sort: "date" | reverse %}

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

        <a href="{{ post.url | relative_url }}" class="read-more">Read More →</a>
      </div>
    </article>
  {% endfor %}
</div>

{% if blog_posts.size == 0 %}
  <p class="text-center py-5">暂无 Blog 文章</p>
{% endif %}
