---
layout: default
permalink: /posts
title: Posts
---

<h1>{{page.title}}</h1>
<div class="posts">
  {% for post in site.categories['post'] %}
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
      <a href="{{ site.baseurl }}{{ post.url }}" class="read-more">Read More</a>
    </article>
    {% endunless %}
  {% endfor %}
</div>
