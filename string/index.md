---
layout: default
title: Baekjoon | Solution Code
---

<h1>Baekjoon</h1>
<hr/>

{% for category in site.categories %}
{% if category[0] == "string" %}
    {% for posts in category %}
    {% for post in posts %}
{% if post.title %}

		{% if post.custom-link %}
<h2><a href="{{ post.custom-link }}"><small>{{ post.date | date: "%d %B, %Y" }}</small>{{ post.title }}</a></h2>
		{% else %}
<h2><a href="{{ post.url }}"><small>{{ post.date | date: "%d %B, %Y" }}</small>{{ post.title }}</a></h2>
		{% endif %}
<hr/>

{% endif %}
   {% endfor %}
   {% endfor %}
{% endif %}
{% endfor %}
