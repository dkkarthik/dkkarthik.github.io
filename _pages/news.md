---
layout: page
title: News
permalink: /news/
nav: true
nav_order: 3
---

<div class="news-list" markdown="1">

{% assign announcements = site.news | sort: "order" %}
{% assign years = announcements | group_by: "year" %}
{% for year in years %}
## {{ year.name }}
{% for item in year.items %}
{% if item.image %}
<div class="news-item has-media">
<img class="news-thumb" src="{{ item.image | relative_url }}" alt="{{ item.image_alt | escape }}" loading="lazy" data-zoomable>
<div class="news-body" markdown="1">

{{ item.content }}

</div>
</div>
{% else %}
{{ item.content }}
{% endif %}
{% endfor %}
{% endfor %}

</div>
