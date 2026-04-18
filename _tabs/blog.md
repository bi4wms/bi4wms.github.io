---
title: Blog
layout: page
permalink: /blog/
icon: fas fa-newspaper
order: 6
---
<style>
/* 精确对齐 Chirpy 官方首页卡片风格 */
.card-title {
    font-size: 1.25rem !important;     /* 首页卡片标题大小 */
    line-height: 1.35 !important;
    margin-top: 0.25rem !important;    /* 大幅减少标题上方留白（原问题核心） */
    margin-bottom: 0.65rem !important;
}

.card-body {
    padding: 1.35rem 1.4rem !important;
}

/* 卡片间距与首页保持一致 */
.post-list {
    gap: 1.55rem !important;           /* 比原来 2rem 更紧凑 */
}

.post-list .card {
    margin-top: 0 !important;
    transition: all 0.2s ease;
}

.post-list .card:hover {
    transform: translateY(-3px);
    box-shadow: var(--card-shadow, 0 8px 25px rgba(0,0,0,0.15)) !important;
}

/* 让文字颜色和首页一致 */
.card-text {
    color: var(--text-muted) !important;
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
          
          {% if post.tags.size > 0 %}
            • 
            {% for tag in post.tags limit: 4 %}
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
  <p class="text-center py-5">暂无 Blog 文章</p>
{% endif %}
