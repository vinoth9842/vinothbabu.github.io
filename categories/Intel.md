---
layout: page
permalink: /blog/categories/Intel
---

<h3> Posts by Category : {{ page.title }} </h3>

<div class="card">
{% for post in site.categories.Intel %}
 <li class="category-posts"><span>{{ post.date | date_to_string }}</span> &nbsp; <a href="{{ post.url }}">{{ post.title }}</a></li>
{% endfor %}
</div>
