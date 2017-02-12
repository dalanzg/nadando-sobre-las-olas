---
layout: page
title: Posts por categorías
description: Posts ordenados por categorías.
---

<div class="card">
  <div class="card-header"><h1>Categorías</h1></div>
  <div class="card-block">
    {% assign tags = site.tags | sort %}
    {% assign sorted_posts = site.posts | sort: 'title' %}

    <div> 
      {% for tag in tags %}
      <a href="#{{ tag | first | slugify }}">{{ tag | first | replace: '-', ' ' }} <span class="badge badge-default">{{ tag | last | size }}</span></a>{% if forloop.last == false %} • {% endif %}{% endfor %}
    </div>
  </div>

  <hr>

  <div class="card-block">
    {% for tag in tags %}
    <p><a name="{{ tag | first | slugify }}"></a>&nbsp;</p>
    <h3 class="archivetitle">
      <span>
        <i class="fa fa-tag" aria-hidden="true"></i>
      </span>
      <span>
        {{ tag | first | replace:'-', ' ' }} 
      </span>
      <span class="badge badge-default">{{ tag | last | size }}</span>
    </h3>

    <ul>
      {% for post in sorted_posts %}
      {% if post.tags contains tag[0] %}
      <li>
        <a href="{{ post.url | prepend: site.baseurl }}">{{ post.title }}</a>
        <span class="text-muted">{% if post.date %} • {{ post.date | date: "%d/%m/%Y" }}{% endif %}</span>
      </li>
      {% endif %}
      {% endfor %}
    </ul>
    {% endfor %}
  </div>
</div>
