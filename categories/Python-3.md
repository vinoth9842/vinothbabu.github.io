---
layout: page
permalink: /blog/categories/Python-3
---

<h3> Posts by Category : {{ page.title }} </h3>

<div class="card">
{% for post in site.categories.Python-3 %}
 <li class="category-posts"><span>{{ post.date | date_to_string }}</span> &nbsp; <a href="{{ post.url }}">{{ post.title }}</a></li>
{% endfor %}
</div>
