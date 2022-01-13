---
layout: default
permalink: /live
title: The Live Page
---
{% assign posts = false %}
<h1>{{page.title}}</h1>
<div class="posts">
  {% for post in site.categories['live'] %}
  {% unless post.hidden == true %}
  {% assign posts = true %}
<article style="{% if post.categories contains "video" %}background-color: rgb(81, 180, 250); {% elsif post.categories contains "podcast" or post.categories contains "radio" %}background-color: rgb(138, 234, 146); {% elsif post.categories contains "update" %}background-color: rgba(255,128,0,0.25); {% endif %}padding: 1em;" class="post">
      {% if post.published == false %}
      <div class="post-unpublished">
        <p class="split">Unpublished</p>
      </div>
      {% endif %}
      {% if post.artwork <> Null %}
      <div style="display: grid; grid-template-columns: repeat(3, minmax(0, 1fr)); text-align: center; grid-gap: 1rem; margin:15px 0">
        <div style="display: flex; flex-direction: column; height: 100%; justify-content: center; align-items: center;"><img height=auto width="200" style="vertical-align:middle;" src="{{post.artwork}}"></div>
        <div style="grid-column-start: 2; grid-column-end: 4; display: flex; flex-direction: column; height: 100%; justify-content: center;">
      {% endif %}
      <a href="{{ site.baseurl }}{{ post.url }}">
        <h1 style="margin-top: 0;">{% if post.categories contains "podcast" or post.categories contains "radio" %}{{post.show}}{% else %}{{ post.title }}{% endif %}</h1>
        {% if post.categories contains "podcast" or post.categories contains "radio" %}
          {% assign titlelc = post.title | downcase %}
          {% assign showlc = post.show | downcase %}
          <h2 style="margin: 0;">{% unless post.season == Null %}Season {{ post.season }}{% endunless %}{% unless post.season == Null or post.episode == Null and titlelc == showlc %}: {% endunless %}{% unless post.episode == Null %}#{{ post.episode }}{% endunless %}{% unless post.episode == Null or titlelc == showlc %} - {% endunless %}{% unless titlelc == showlc %}{{ post.title }}{% endunless %}</h2>
        {% endif %}
      </a>
      <div class="post-elsewhere">
        {% if post.elsewhere %}<p style="text-align: center;">🔀 from {{post.elsewhere}}</p>{% endif %}
      </div>
      {% if post.artwork <> Null %}
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
      </div>
        </div>
      {% endif %}
      {% unless post.categories contains "podcast" or post.categories contains "radio" %}
      <div class="entry">
        {{ post.excerpt }}
      </div>
      {% endunless %}
      {% if post.show-excerpt == 'excerpt' %}
    <div class="entry">
      {{ post.excerpt }}
    </div>
    {% elsif post.mp3 <> Null and post.youtube <> Null %}
    {% if post.show-excerpt == 'mp3' %}
    <div style="text-align:center">
      <audio controls style="width: 75%;">
        <source src="{{ post.mp3 }}" type="audio/mpeg">
        Your browser does not support the audio element.
      </audio>
      </div>
      {% elsif post.show-excerpt == 'youtube' %}
      <iframe width="100%" height="400em" src="https://www.youtube.com/embed/{{ post.youtube }}" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
      {% endif %}
     {% else %}
      {% if post.mp3 <> Null %}
      <div style="text-align:center">
      <audio controls style="width: 75%;">
        <source src="{{ post.mp3 }}" type="audio/mpeg">
        Your browser does not support the audio element.
      </audio>
      </div>
      {% elsif post.youtube <> Null %}
      <iframe width="100%" height="400em" src="https://www.youtube.com/embed/{{ post.youtube }}" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
      {% else %}
      <div class="entry">
        {{ post.excerpt }}
      </div>
      {% endif %}
      {% endif %}
      {% unless post.artwork <> Null %}
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
      {% endunless %}
      {% if post.categories contains "podcast" or post.categories contains "radio" %}<a href="{{ site.baseurl }}{{ post.url }}" class="read-more">Show Notes</a>{% elsif post.categories contains "video" or post.categories contains "live" %}{% else %}<a href="{{ site.baseurl }}{{ post.url }}" class="read-more">Read More</a>{% endif %}
    </article>
  {% endunless %}
  {% endfor %}
  {% if posts == false %}
  <p style="text-align:center;" ><br />Oops, there's nothing here at the moment!<br /><br />If I'm live blogging an event or doing a livestream, it'll show up here<br /><br />In the meantime, you can go back to the <a href="{{ site.baseurl }}/">main page</a></p>
  {% endif %}
