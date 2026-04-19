---
icon: fas fa-server
order: 4
---

{% assign wanted_parent = "Platforms" %}
<div class="categories">
  {% for cat in site.categories %}
    {% assign parent = cat[0] %}

    {% if parent == wanted_parent %}
      <div class="category">
        <h2>
          {{ parent }}
          <small>({{ cat[1].size }} posts)</small>
        </h2>

        <!-- 收集子分类（去重 + 排序） -->
        {% assign subcats = "" | split: "," %}
        {% for post in cat[1] %}
          {% if post.categories.size > 1 %}
            {% assign sub = post.categories[1] %}
            {% unless subcats contains sub or sub == parent %}
              {% assign subcats = subcats | push: sub %}
            {% endunless %}
          {% endif %}
        {% endfor %}

        {% if subcats.size > 0 %}
          <ul class="subcategories">
            {% for sub in subcats | sort %}
              <li>
                <a href="{{ site.baseurl }}/categories/{{ sub | slugify }}/">
                  {{ sub }}
                </a>
                <small>({{ site.categories[sub] | size | default: 0 }} posts)</small>
              </li>
            {% endfor %}
          </ul>
        {% endif %}
      </div>
    {% endif %}
  {% endfor %}
</div>
