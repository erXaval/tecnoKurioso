---
layout: page
title: Archivo
permalink: /archivo/
---

Todas las entradas de TecnoKurioso, de la más reciente a la más antigua.

{% assign por_anio = site.posts | group_by_exp: "post", "post.date | date: '%Y'" %}
{% for grupo in por_anio %}
<h2 class="archive-year">{{ grupo.name }}</h2>
<ul class="archive-list">
  {% for post in grupo.items %}
  <li>
    <time datetime="{{ post.date | date_to_xmlschema }}">{{ post.date | date: "%d/%m" }}</time>
    <a href="{{ post.url | relative_url }}">{{ post.title | escape }}</a>
    {% include chip-seccion.html categoria=post.categories.first %}
  </li>
  {% endfor %}
</ul>
{% endfor %}
