---
layout: page
title: Archivo
description: Posts ordenados por fecha.
---

<div class="card">
  <div class="card-header"><h1>Archivo</h1></div>
  <div class="card-block">

{% for post in site.posts %}
{% capture this_year %}{{ post.date | date: "%Y" }}{% endcapture %}
{% capture this_month %}
  {% assign this_month = post.date | date: '%-m' %}
  {% case this_month %}
    {% when '1' %}Enero
    {% when '2' %}Febrero
    {% when '3' %}Marzo
    {% when '4' %}Abril
    {% when '5' %}Mayo
    {% when '6' %}Junio
    {% when '7' %}Julio
    {% when '8' %}Agosto
    {% when '9' %}Septiembre
    {% when '10' %}Octubre
    {% when '11' %}Noviembre
    {% when '12' %}Diciembre
  {% endcase %}
{% endcapture %}
{% capture next_year %}{{ post.previous.date | date: "%Y" }}{% endcapture %}
{% capture next_month %}
  {% assign next_month = post.previous.date | date: '%-m' %}
  {% case next_month %}
    {% when '1' %}Enero
    {% when '2' %}Febrero
    {% when '3' %}Marzo
    {% when '4' %}Abril
    {% when '5' %}Mayo
    {% when '6' %}Junio
    {% when '7' %}Julio
    {% when '8' %}Agosto
    {% when '9' %}Septiembre
    {% when '10' %}Octubre
    {% when '11' %}Noviembre
    {% when '12' %}Diciembre
  {% endcase %}
{% endcapture %}

{% if forloop.first %}
    <div class="card">
      <div class="card-header"><h4>Año {{ this_year }}</h4></div>
      <div class="card-block">
        <h5>{{ this_month }}</h5>
        <ul>
{% endif %}
          <li>
            <a href="{{ post.url | prepend: site.baseurl }}">{{ post.title }}</a>  •  <span>{{ post.date | date: "%d/%m/%Y" }}</span>
          </li>
{% if forloop.last %}
        </ul>
      </div>
    </div>
{% else %}
  {% if this_year != next_year %}
        </ul>
      </div>
    </div>
    <div class="card">
      <div class="card-header"><h4>Año {{ next_year }}</h4></div>
      <div class="card-block">
        <h5>{{ next_month }}</h5>
        <ul>
  {% else %}
    {% if this_month != next_month %}
        </ul>
        <h5>{{ next_month }}</h5>
        <ul>
    {% endif %}
  {% endif %}
{% endif %}
{% endfor %}

  </div>
</div>
