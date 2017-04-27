---
layout: page
title: Projects
pagination:
  enabled: true
  tag: project
---

{% include filter_by_tag.html %}

{% for post in site.posts %}{{ post.date | date_to_string }} &raquo; [ {{ post.title }} ]({{ post.url }})  
{% endfor %}
