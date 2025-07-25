---
layout: page
title: Tags
permalink: /tags/
---

## 🏷️ 标签分类

按技术主题和标签分类查看文章。

---

{% if site.tags.size > 0 %}
  {% assign sorted_tags = site.tags | sort %}
  {% for tag in sorted_tags %}
    {% assign tag_name = tag[0] %}
    {% assign tag_posts = tag[1] %}
    
<h3 id="{{ tag_name | slugify }}">
  <span class="tag-icon">#</span>{{ tag_name }}
  <span class="tag-count">({{ tag_posts.size }})</span>
</h3>

<ul class="tag-post-list">
{% for post in tag_posts %}
  <li>
    <span class="post-date">{{ post.date | date: "%Y-%m-%d" }}</span>
    <a href="{{ post.url | relative_url }}">{{ post.title }}</a>
  </li>
{% endfor %}
</ul>
  {% endfor %}
{% endif %}

{% if site.tags.size == 0 %}
<p><em>还没有标签分类的文章...</em></p>
{% endif %}

## 📊 标签云

<div class="tag-cloud">
{% if site.tags.size > 0 %}
  {% assign sorted_tags = site.tags | sort %}
  {% for tag in sorted_tags %}
    {% assign tag_name = tag[0] %}
    {% assign tag_posts = tag[1] %}
    {% assign tag_size = tag_posts.size %}
    {% if tag_size > 3 %}
      {% assign class = "tag-large" %}
    {% elsif tag_size > 1 %}
      {% assign class = "tag-medium" %}
    {% else %}
      {% assign class = "tag-small" %}
    {% endif %}
    
<a href="#{{ tag_name | slugify }}" class="tag-link {{ class }}">{{ tag_name }}</a>
  {% endfor %}
{% endif %}
</div>

<style>
.tag-icon {
  color: #007acc;
  margin-right: 5px;
}

.tag-count {
  color: #666;
  font-size: 0.9em;
  font-weight: normal;
}

.tag-post-list {
  margin-bottom: 30px;
}

.tag-post-list li {
  margin-bottom: 8px;
}

.post-date {
  color: #666;
  font-size: 0.9em;
  margin-right: 15px;
  font-family: 'Monaco', 'Menlo', monospace;
}

.tag-cloud {
  margin-top: 20px;
  padding: 20px;
  background: #f8f9fa;
  border-radius: 8px;
}

.tag-link {
  display: inline-block;
  margin: 5px 8px 5px 0;
  padding: 4px 8px;
  background: #e9ecef;
  border-radius: 4px;
  text-decoration: none;
  color: #495057;
  transition: all 0.2s ease;
}

.tag-link:hover {
  background: #007acc;
  color: white;
  text-decoration: none;
}

.tag-large {
  font-size: 1.1em;
  font-weight: bold;
}

.tag-medium {
  font-size: 1em;
}

.tag-small {
  font-size: 0.9em;
  color: #6c757d;
}
</style> 