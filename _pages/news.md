---
layout: page
title: News
permalink: /news/
nav: true
nav_order: 3
---

{% assign announcements = site.news | sort: "order" %}
{% assign years = announcements | group_by: "year" %}
{% for year in years %}
## {{ year.name }}
{% for item in year.items %}
{{ item.content }}
{% endfor %}
{% endfor %}
