---
layout: default
title: 삼성 SW Expert Academy | Solution code
---

<h1>D1 Solution code</h1>
<hr/>

{% for category in site.categories %}
{% if category[0] == "d1" %}
    {% for posts in category %}
    {% for post in posts %}
{% if post.title %}

		{% if post.custom-link %}
<h2><a href="{{ post.custom-link }}"><small>{{ post.date | date: "%d %B, %Y" }}</small>{{ post.title }}</a></h2>
		{% else %}
<h2><a href="{{ post.url }}"><small>{{ post.date | date: "%d %B, %Y" }}</small>{{ post.title }}</a></h2>
		{% endif %}
<p>{{ post.excerpt | truncatewords:50 }}</p>
<hr/>

{% endif %}
   {% endfor %}
   {% endfor %}
{% endif %}
{% endfor %}