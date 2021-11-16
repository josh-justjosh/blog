---
layout: page
permalink: /roles/
title: Roles
date: 2021-12-31
---

{% assign roles = '' %}
{% for i in site.posts %}
{% for j in i.roles %}
{% assign roles = roles | append: j %}
{% assign roles = roles | append: ', ' %}
{%endfor%}
{%endfor%}
{% assign roles = roles | split: ", " | uniq | sort %}

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
      {% assign titlelc = post.title | downcase %}
      {% assign showlc = post.show | downcase %}
    <p><center><b><a href="{{ site.baseurl }}{{ post.url }}">{% if post.title and post.title != "" %}{% if post.categories contains "podcast" %}{{ post.show }}: {% unless post.season == Null %}Season {{ post.season }}{% endunless %}{% unless post.season == Null or post.episode == Null and titlelc == showlc %}: {% endunless %}{% unless post.episode == Null %}#{{ post.episode }}{% endunless %}{% unless post.episode == Null or titlelc == showlc %} - {% endunless %}{% unless titlelc == showlc %}{{ post.title }}{% endunless %}{% else %}{{post.title}}{% endif %}{% else %}{{post.excerpt |strip_html}}{%endif%}</a></b> - {% if post.date and post.date != "" %}{{ post.date | date: "%e %B %Y" }}{%endif%}</center></p>
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
