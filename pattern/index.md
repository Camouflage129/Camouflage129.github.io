---
layout: default
title: Baekjoon | Solution Code
---

<h1>Baekjoon</h1><hr/>

{% for category in site.categories %}
{% if category[0] == "pattern" %}
    {% for posts in category %}
    {% for post in posts %}
{% if post.title %}

```
	{% if post.custom-link %}
```

<h2><a href="{{ post.custom-link }}"><small>{{ post.date | date: "%d %B, %Y" }}</small>{{ post.title }}</a></h2>

{% if site.discus-identifier %}
 <a href="{{ site.url }}{{ site.baseurl }}{{ post.url }}#disqus_thread" data-disqus-identifier="{{ post.id }}"></a>
{% endif %}

{% else %}
<h2><a href="{{ post.url }}"><small>{{ post.date | date: "%d %B, %Y" }}</small>{{ post.title }}</a></h2>

{% if site.discus-identifier %}
 <a href="{{ site.url }}{{ site.baseurl }}{{ post.url }}#disqus_thread" data-disqus-identifier="{{ post.id }}"></a>
{% endif %}

{% endif %}
<p>{{ post.excerpt | truncatewords:25 }}</p>
<hr/>

{% endif %}
   {% endfor %}
   {% endfor %}
{% endif %}
{% endfor %}