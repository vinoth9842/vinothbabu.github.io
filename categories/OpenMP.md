---
layout: page
permalink: /blog/categories/OpenMP
---

<h3> Posts by Category : {{ page.title }} </h3>

<div class="card">
{% for post in site.categories.OpenMP %}
 <li class="category-posts"><span>{{ post.date | date_to_string }}</span> &nbsp; <a href="{{ post.url }}">{{ post.title }}</a></li>
{% endfor %}
</div>
