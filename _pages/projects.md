---
layout: page
title: Projects
permalink: /projects/
description: Research in robot autonomy, perception, and sensing.
nav: true
nav_order: 1
---

<style>
  .projects .card-img-top {
    width: 100%;
    height: 240px;
    object-fit: contain;
    background: white;
  }
</style>

<div class="projects">
{% assign sorted_projects = site.projects | sort: "importance" %}
<div class="row row-cols-1 row-cols-md-2">
{% for project in sorted_projects %}
{% include projects.liquid %}
{% endfor %}
</div>
</div>
