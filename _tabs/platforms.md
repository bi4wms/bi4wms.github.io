---
layout: categories
icon: fas fa-server
order: 4
---

{% assign wanted_categories = "Platforms" | split: "|" %}   <!-- ← 这里改成你想显示的关键字，用 | 分隔 -->

<h1 class="page-title">{{ page.title }}</h1>

<div class="categories">
  {% for category in site.categories %}
    {% if wanted_categories contains category[0] %}
      <div class="category">
        <h2 id="{{ category[0] | slugify }}">
          <a href="{{ site.baseurl }}/categories/{{ category[0] | slugify }}/">
            {{ category[0] }}
          </a>
          <small>({{ category[1].size }} posts)</small>
        </h2>
        <!-- 如果你想显示子分类，可以继续加逻辑 -->
      </div>
    {% endif %}
  {% endfor %}
</div>
