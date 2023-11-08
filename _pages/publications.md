---
layout: page
permalink: /publications/
title: publications
description: publications by categories in reversed chronological order  <br> *equal contribution
years1: [2023, 2021]
years2: [2021, 2020]
nav: true
nav_order: 1
---
<!-- _pages/publications.md -->
<div class="publications">

<h1>preprints</h1>

{% bibliography -f preprints %}

<h1>conference &amp; journal articles</h1>

{% for y in page.years1 %}
  <h2 class="year">{{y}}</h2>
  {% bibliography -f papers -q @*[year={{y}}]* %}
{% endfor %}

<h1>technical reports &amp; short papers</h1>

{% for y in page.years2 %}
  <h2 class="year">{{y}}</h2>
  {% bibliography -f reports -q @*[year={{y}}]* %}
{% endfor %}

</div>
