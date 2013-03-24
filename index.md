---
layout: page
---

<ul class="posts">
  {% for post in site.posts %}
    <li><h1>{{ post.title }}<small>{{ post.date | date_to_string }}</small></h1></li>
    <li class="excerpt">{{ post.content | strip_html | truncatewords:75}}</li>
    <li class="excerpt-link"><a href="{{ post.url }}">Read more...</a><br></li>
    <hr>
  {% endfor %}
</ul>


