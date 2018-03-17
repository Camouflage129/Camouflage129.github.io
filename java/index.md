---
layout: default
title: Java | Spring / Framework
---

<h1>Java</h1>
<hr/>

{% for category in site.categories %}
{% if category[0] == "java" %}
    {% for posts in category %}
    {% for post in posts %}
{% if post.title %}

		{% if post.custom-link %}
<h2><a href="{{ post.custom-link }}"><small>{{ post.date | date: "%d %B, %Y" }}</small>{{ post.title }}</a></h2>

<a href="https://disqus.com/embed/comments/?base=default&f={{ site.discus-identifier }}&t_i=/{{ post.custom-link }}&t_u=https://camouflage129.github.io/{{ post.custom-link }}&t_d={{ post.title }}&t_t={{ post.title }}&s_o=default#version=3e91f895da97667a42583677a655c093">test</a>

{% if site.discus-identifier %}
 <a href="{{ site.url }}{{ site.baseurl }}{{ post.url }}#disqus_thread" data-disqus-identifier="{{ post.id }}"></a>
{% endif %}

{% else %}
<h2><a href="{{ post.url }}"><small>{{ post.date | date: "%d %B, %Y" }}</small>{{ post.title }}</a></h2>

<a href="https://disqus.com/embed/comments/?base=default&f={{ site.discus-identifier }}&t_i=/{{ post.custom-link }}&t_u=https://camouflage129.github.io/{{ post.custom-link }}&t_d={{ post.title }}&t_t={{ post.title }}&s_o=default#version=3e91f895da97667a42583677a655c093">test</a>

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