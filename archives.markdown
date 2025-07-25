---
layout: page
title: Archives
permalink: /archives/
---

## 📚 文章归档

这里收录了我写过的所有技术文章，按时间倒序排列。

---

{% assign posts_by_year = site.posts | group_by_exp: "post", "post.date | date: '%Y年%m月'" %}

{% for year_group in posts_by_year %}
<h3>{{ year_group.name }}</h3>
<ul>
  {% for post in year_group.items %}
  <li>
    <span class="post-date">{{ post.date | date: "%m月%d日" }}</span>
    <a href="{{ post.url | relative_url }}">{{ post.title }}</a>
    {% if post.categories.size > 0 %}
      <span class="post-categories">
        {% for category in post.categories %}
          <span class="category">{{ category }}</span>
        {% endfor %}
      </span>
    {% endif %}
  </li>
  {% endfor %}
</ul>
{% endfor %}

{% if site.posts.size == 0 %}
<p><em>还没有发布任何文章...</em></p>
{% endif %}

<style>
.post-date {
  color: #666;
  font-size: 0.9em;
  margin-right: 10px;
}
.post-categories {
  margin-left: 10px;
}
.category {
  background: #e9ecef;
  padding: 2px 6px;
  border-radius: 3px;
  font-size: 0.8em;
  margin-right: 5px;
}
</style> 