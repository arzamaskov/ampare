---
bg: "card-catalogue.jpg"
layout: page
permalink: /posts/
title: "Архив"
crawlertitle: "Архив материалов"
summary: "подборки материалов по категориям"
active: archive
---

<div class="search">
  <i class="icon icon-search"></i>
  <input type="text" id="search-input" class="input" placeholder="поиск..">
  <ul id="results-container" class="dropdown"></ul>
</div>

{% for tag in site.tags %}
  {% assign t = tag | first %}
  {% assign posts = tag | last %}

  <h2 class="category-key" id="{{ t | downcase }}">{{ t | capitalize }}</h2>

  <ul class="year">
    {% for post in posts %}
      {% if post.tags contains t %}
        <li>
          {% if post.lastmod %}
            <a href="{{ post.url | relative_url}}">{{ post.title }}</a>
            <span class="date">{{ post.lastmod | date: "%d-%m-%Y"  }}</span>
          {% else %}
            <a href="{{ post.url | relative_url}}">{{ post.title }}</a>
            <span class="date">{{ post.date | date: "%d-%m-%Y"  }}</span>
          {% endif %}
        </li>
      {% endif %}
    {% endfor %}
  </ul>

{% endfor %}
