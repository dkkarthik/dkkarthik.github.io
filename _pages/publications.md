---
layout: page
title: Publications
permalink: /publications/
nav: true
nav_order: 2
---

<section class="publications" aria-labelledby="journal-publications">
  <h2 id="journal-publications">Journal Publications</h2>
  {% bibliography --query @article --group_by none %}
</section>

<section class="publications" aria-labelledby="conference-publications">
  <h2 id="conference-publications">Conference Publications</h2>
  {% bibliography --query @inproceedings --group_by none %}
</section>

<section class="publications" aria-labelledby="preprints-other-publications">
  <h2 id="preprints-other-publications">Preprints and Other Publications</h2>
  {% bibliography --query @misc --group_by none %}
</section>
