---
title: Guides
layout: page
icon: fas fa-book-open
permalink: /guides/
order: 7
---
{% assign blog_posts = site.posts | where_exp: "post", "post.categories contains 'Tutorial'" | sort: "date" | reverse %}

<div class="post-list" style="display: flex; flex-direction: column; gap: 2rem;">
  {% for post in blog_posts %}
    <article class="card" 
             style="background-color: var(--card-bg, #ffffff); 
                    border: 1px solid var(--border-color, #e5e7eb); 
                    color: var(--text-color, #1f2937);">
      <div class="card-body">
        <h2 class="card-title">
          <a href="{{ post.url | relative_url }}">{{ post.title }}</a>
        </h2>

        {% if post.description %}
          <p class="card-text" style="color: var(--text-muted, #6b7280);">{{ post.description }}</p>
        {% elsif post.excerpt %}
          <p class="card-text" style="color: var(--text-muted, #6b7280);">{{ post.excerpt | strip_html | truncate: 180 }}</p>
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

        <a href="{{ post.url | relative_url }}" class="read-more">Read More... →</a>
      </div>
    </article>
  {% endfor %}
</div>

{% if blog_posts.size == 0 %}
  <p class="text-center py-5">暂无 Blog 文章</p>
{% endif %}
