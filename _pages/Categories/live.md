---
layout: default
permalink: /live
title: The Live Page
date: 2021-12-31
---
{% assign posts = false %}
<h1>{{page.title}}</h1>
<div class="posts">
  {% for post in site.categories['live'] %}
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
    </article>
    {% assign posts = true %}
    {% endunless %}
  {% endfor %}
  {% if posts == false %}
  <p style="text-align:center;" ><br />Oops, there's nothing here at the moment!<br /><br />If I'm live blogging an event or doing a livestream, it'll show up here<br /><br />In the meantime, you can go back to the <a href="https://blog.josh.me.uk/live">main page</a></p>
  {% endif %}
</div>