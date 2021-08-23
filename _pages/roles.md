---
layout: page
permalink: /roles/
title: Roles
date: 2021-12-31
---

{% assign roles = 'Vision Mixer, Camera Operator, Video Editor, Runner' | split: ', ' | sort %}

<div id="archives">
{% for role in roles %}
{% assign posts = false %}
  <div class="archive-group">
  <div id="#{{ role | slugize }}"></div>
  <p></p>
  <h3 style="text-transform: capitalize;" class="category-head">{{ role }}</h3>
  <a name="{{ role | slugize }}"></a>
  {% for post in site.posts %}
  {% if post.roles contains role %}
  {% unless post.hidden == true %}
  <article class="archive-item">
    <p><center><b><a href="{{ site.baseurl }}{{ post.url }}">{% if post.title and post.title != "" %}{{post.title}}{% else %}{{post.excerpt |strip_html}}{%endif%}</a></b> - {% if post.date and post.date != "" %}{{ post.date | date: "%e %B %Y" }}{%endif%}</center></p>
    </article>
    {% assign posts = true %}
  {% endunless %}
  {% endif %}
  {% endfor %}
    {% if posts == false %}
    <p style="text-align:center;">This Role is Empty</p>
    {% endif %}
  </div>
{% endfor %}
</div>
