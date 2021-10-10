---
layout: default
permalink: /videos
title: Videos
date: 2021-12-31
---

<h1>{{page.title}}</h1>
<div class="posts">
  {% for post in site.categories['video'] %}
    {% unless post.hidden == true %}
    <article style="padding: 1em;" class="post">
      <a href="{{ site.baseurl }}{{ post.url }}">
        <h1 style="margin-top: 0;">{{ post.title }}</h1>

        <div>
          <p class="post_date">{{ post.date | date: "%e %B %Y" }}</p>
        </div>
      </a>
      {% if post.elsewhere %}<p style="text-align: center;">🔀 from {{post.elsewhere}}</p>{% endif %}
      <div class="entry">
        {{ post.excerpt }}
      </div>
      <div class="post-roles">
        {% if post %}
          {% assign roles = post.roles %}
        {% else %}
          {% assign roles = page.roles %}
        {% endif %}
        {% for role in roles %}
          <a href="{{site.baseurl}}/roles/#{{role|slugize}}">{{role | replace: " ", "&nbsp;"}}</a>
          {% unless forloop.last %}&nbsp;{% endunless %}
        {% endfor %}
      </div>
    </article>
    {% endunless %}
  {% endfor %}
</div>
