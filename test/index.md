---
layout: default
title: 삼성 SW Expert Academy | Solution code
---

<h1>모의 SW 역량테스트</h1>
<hr/>

{% for category in site.categories %}
{% if category[0] == "test" %}
    {% for posts in category %}
    {% for post in posts %}
{% if post.title %}

		{% if post.custom-link %}
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
<hr/>

{% endif %}
   {% endfor %}
   {% endfor %}
{% endif %}
{% endfor %}