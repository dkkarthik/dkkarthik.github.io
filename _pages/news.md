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
<span class="news-thumb-wrap" style="--focus: {{ item.image_focus | default: '50%' }}; --ratio: {{ item.image_ratio | default: 1.78 }}"><img class="news-thumb" src="{{ item.image | relative_url }}" alt="{{ item.image_alt | escape }}" loading="lazy" data-zoomable></span>
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
