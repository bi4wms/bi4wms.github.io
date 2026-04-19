---
layout: categories
icon: fas fa-server
order: 4
---

{% assign wanted_parent = "Platforms" %}   <!-- ← 只改这里即可，改成你的大分类名称（区分大小写） -->

<h1 class="page-title">{{ page.title }}</h1>

<div class="categories">
  {% for cat in site.categories %}
    {% assign parent = cat[0] %}   <!-- 第一个元素是大分类 -->

    {% if parent == wanted_parent %}
      <div class="category">
        <h2 id="{{ parent | slugify }}">
          <a href="{{ site.baseurl }}/categories/{{ parent | slugify }}/">
            {{ parent }}
          </a>
          <small>({{ cat[1].size }} posts)</small>
        </h2>

        <!-- 显示子分类（去重并排序） -->
        {% assign subcats = "" | split: "," %}
        {% for post in cat[1] %}
          {% if post.categories.size > 1 %}
            {% assign sub = post.categories[1] %}
            {% unless subcats contains sub %}
              {% assign subcats = subcats | push: sub %}
            {% endunless %}
          {% endif %}
        {% endfor %}

        {% if subcats.size > 0 %}
          <ul class="subcategories">
            {% for sub in subcats %}
              <li>
                <a href="{{ site.baseurl }}/categories/{{ sub | slugify }}/">
                  {{ sub }}
                </a>
                <!-- 子分类文章数量（简化统计） -->
                <small>({{ site.categories[sub] | size }} posts)</small>
              </li>
            {% endfor %}
          </ul>
        {% endif %}
      </div>
    {% endif %}
  {% endfor %}
</div>
