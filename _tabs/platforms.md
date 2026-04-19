---
title: Platforms
icon: fas fa-server
order: 4
---
{% assign wanted_parent = "Platforms" %}

<h1 class="page-title">{{ page.title }}</h1>

{% for cat in site.categories %}
  {% assign parent = cat[0] %}

  {% if parent == wanted_parent %}
    {% assign posts_of_category = cat[1] %}
    {% assign first_post = posts_of_category | first %}

    {% assign sub_categories = '' | split: '' %}
    {% for post in posts_of_category %}
      {% if post.categories.size > 1 %}
        {% assign sub = post.categories[1] %}
        {% unless sub_categories contains sub %}
          {% assign sub_categories = sub_categories | push: sub %}
        {% endunless %}
      {% endif %}
    {% endfor %}
    {% assign sub_categories = sub_categories | sort %}
    {% assign sub_size = sub_categories | size %}
    {% assign total_posts = posts_of_category | size %}

    <!-- 模仿官方 card 样式 -->
    <div class="card categories">
      <div class="card-header d-flex justify-content-between hide-border-bottom">
        <span class="ms-2">
          <i class="far fa-folder-open fa-fw"></i>
          <span class="mx-2">{{ parent }}</span>
          <span class="text-muted small font-weight-light">
            {% if sub_size > 0 %}
              {{ sub_size }} categories,
            {% endif %}
            {{ total_posts }} posts
          </span>
        </span>
      </div>

      <!-- 子分类列表（官方风格） -->
      {% if sub_size > 0 %}
        <div class="collapse show">
          <ul class="list-group">
            {% for sub in sub_categories %}
              <li class="list-group-item">
                <i class="far fa-folder fa-fw"></i>
                <a href="{{ site.baseurl }}/categories/{{ sub | slugify | url_encode }}/" class="mx-2">{{ sub }}</a>
                <span class="text-muted small font-weight-light">
                  {% assign sub_posts = site.categories[sub] | size | default: 0 %}
                  {{ sub_posts }}
                  {% if sub_posts > 1 %}posts{% else %}post{% endif %}
                </span>
              </li>
            {% endfor %}
          </ul>
        </div>
      {% endif %}
    </div>
  {% endif %}
{% endfor %}
