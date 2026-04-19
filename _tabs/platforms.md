---
title: Platforms
icon: fas fa-server
order: 4
---

<h1 class="page-title">{{ page.title }}</h1>

{% assign wanted_parent = "Platforms" %}

{% for cat in site.categories %}
  {% if cat[0] == wanted_parent %}

    <!-- 收集子分类 -->
    {% assign subcats = "" | split: "," %}
    {% for post in cat[1] %}
      {% if post.categories.size > 1 %}
        {% assign sub = post.categories[1] %}
        {% unless subcats contains sub %}
          {% assign subcats = subcats | push: sub %}
        {% endunless %}
      {% endif %}
    {% endfor %}
    {% assign subcats = subcats | sort %}

    <!-- 模仿官方 Categories 卡片样式（去掉多余 Platforms (1 posts)） -->
    <article class="card categories">
      <div class="card-header d-flex justify-content-between align-items-center">
        <span>
          <i class="far fa-folder-open fa-fw"></i>
          <span class="mx-2 h5 mb-0">{{ wanted_parent }}</span>
        </span>
        <i class="fas fa-chevron-down fa-fw"></i>
      </div>

      <div class="collapse show">
        <ul class="list-group list-group-flush">
          {% for sub in subcats %}
            <li class="list-group-item d-flex justify-content-between align-items-center">
              <div>
                <i class="far fa-folder fa-fw"></i>
                <a href="{{ site.baseurl }}/categories/{{ sub | slugify | url_encode }}/" class="mx-2">{{ sub }}</a>
              </div>
              <span class="badge bg-light text-dark rounded-pill">
                {{ site.categories[sub] | size | default: 0 }} 
                {% if site.categories[sub] | size > 1 %}posts{% else %}post{% endif %}
              </span>
            </li>
          {% endfor %}
        </ul>
      </div>
    </article>

  {% endif %}
{% endfor %}
