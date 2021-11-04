---
layout: default
permalink: /podcasts
title: Podcasts
date: 2021-12-31
---

<h1>{{page.title}}</h1>
<div class="posts">
  {% for post in site.categories['podcast'] %}
    {% unless post.hidden == true %}
    <article style="padding: 1em;" class="post">
    <div style="display: grid; grid-template-columns: repeat(3, minmax(0, 1fr)); text-align: center; grid-gap: 1rem; margin:15px 0">
        <div style="display: flex; flex-direction: column; height: 100%; justify-content: center; align-items: center;"><img height=auto width="200" style="vertical-align:middle;" src="{{post.artwork}}"></div>
        <div style="grid-column-start: 2; grid-column-end: 4; display: flex; flex-direction: column; height: 100%; justify-content: center;">
      <a href="{{ site.baseurl }}{{ post.url }}">
        <h1 style="margin-bottom: 0;">{{ post.show }}</h1>
        <h2 style="margin-top: 0;">{% unless post.episode == Null %}#{{ post.episode }} - {% endunless %}"{{ post.title }}"</h2>
        <div>
          <p class="post_date">{{ post.date | date: "%e %B %Y" }}</p>
        </div>
      </a>
      {% if post.elsewhere %}<p style="text-align: center;">🔀 from {{post.elsewhere}}</p>{% endif %}
      <!--<div class="post-roles">
        {% if post %}
          {% assign roles = post.roles %}
        {% else %}
          {% assign roles = page.roles %}
        {% endif %}
        {% for role in roles %}
          <a href="{{site.baseurl}}/roles/#{{role|slugize}}">{{role | replace: " ", "&nbsp;"}}</a>
          {% unless forloop.last %}&nbsp;{% endunless %}
        {% endfor %}
      </div>-->
      </div>
      </div>
      <div style="text-align:center">
      <audio controls style="width: 75%">
        <source src="{{ post.mp3 }}" type="audio/mpeg">
        Your browser does not support the audio element.
      </audio>
      </div>
      <a href="{{ site.baseurl }}{{ post.url }}" class="read-more">Show Notes</a>
    </article>
    {% endunless %}
  {% endfor %}
</div>
