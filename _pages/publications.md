---
layout: page
permalink: /publications/
title: publications
description: publications by categories in reversed chronological order <br> *equal contribution
years1: [2025, 2024, 2023, 2021]
years2: [2025, 2024, 2021, 2020]
nav: true
nav_order: 1
---

<!-- _pages/publications.md -->

<!-- Bibsearch Feature -->

<!-- {% include bib_search.liquid %} -->

<div class="publications">

<h1>preprints</h1>

{% bibliography -f preprints --group_by none %}

<h1>conference &amp; journal articles</h1>

{% for y in page.years1 %}
  <!-- <h2 class="year">{{y}}</h2> -->
  {% bibliography -f papers -q @*[year={{y}}]* %}
{% endfor %}

<h1> short papers &amp; reports  </h1>

{% for y in page.years2 %}
  <!-- <h2 class="year">{{y}}</h2> -->
  {% bibliography -f reports -q @*[year={{y}}]* %}
{% endfor %}

</div>
