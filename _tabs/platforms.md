---
icon: fas fa-server
order: 4
---

<h1 class="page-title">{{ page.title }}</h1>

{% assign wanted_parent = "Platforms" %}

{% for cat in site.categories %}
  {% if cat[0] == wanted_parent %}
    {% assign subcats = "" | split: "," %}

    <!-- 收集所有子分类（去重） -->
    {% for post in cat[1] %}
      {% if post.categories.size > 1 %}
        {% assign sub = post.categories[1] %}
        {% unless subcats contains sub %}
          {% assign subcats = subcats | push: sub %}
        {% endunless %}
      {% endif %}
    {% endfor %}

    {% assign subcats = subcats | sort %}

    <!-- 模仿官方 Categories 卡片样式 -->
    <article class="card categories">
      <div class="card-header d-flex justify-content-between">
        <span>
          <i class="far fa-folder-open fa-fw"></i>
          <span class="mx-2">{{ wanted_parent }}</span>
          <span class="text-muted small">({{ subcats.size }} categories, {{ cat[1].size }} posts)</span>
        </span>
        <i class="fas fa-chevron-down"></i>
      </div>

      <div class="collapse show">
        <ul class="list-group list-group-flush">
          {% for sub in subcats %}
            <li class="list-group-item d-flex justify-content-between align-items-center">
              <span>
                <i class="far fa-folder fa-fw"></i>
                <a href="{{ site.baseurl }}/categories/{{ sub | slugify | url_encode }}/" class="mx-2">{{ sub }}</a>
              </span>
              <span class="badge bg-light text-dark">
                {{ site.categories[sub] | size | default: 0 }} posts
              </span>
            </li>
          {% endfor %}
        </ul>
      </div>
    </article>
  {% endif %}
{% endfor %}
