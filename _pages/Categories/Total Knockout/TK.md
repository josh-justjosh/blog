---
layout: default
permalink: /totalknockout
title: "TK: Total Knockout"
---
<!--<img src="/images/Shared Content/SLLET radio wide.png">-->
<h1>{{page.title}}</h1>
<div style="text-align:center;">
  <a href="/totalknockout/rss"><i class="svg-icon rss"></i></a>
  <!--<a href="https://podcasts.apple.com/us/podcast/the-sllet-radio-show/id1587759816"><i class="svg-icon apple-podcasts"></i></a>
  <a href="https://podcasts.google.com/feed/aHR0cHM6Ly9hbmNob3IuZm0vcy82ZDE5MzFkNC9wb2RjYXN0L3Jzcw"><i class="svg-icon google-podcasts"></i></a>-->
  <a href="https://pca.st/17xn88u9"><i class="svg-icon pocketcasts"></i></a>
  <!--<a href="https://overcast.fm/itunes1587759816"><i class="svg-icon overcast"></i></a>
  <a href="https://open.spotify.com/show/49NzLESoNnQQroy35vPQhW"><i class="svg-icon spotify"></i></a>-->
  <!--<a href="https://www.youtube.com/channel/UClG7zTagAztOx5KhVwPgRVQ"><i class="svg-icon youtube"></i></a>-->
  <!--<i class="svg-icon"></i>
  <!--<a href="https://facebook.com/slletshow"><i class="svg-icon facebook"></i></a>
  <a href="https://instagram.com/slletshow"><i class="svg-icon instagram"></i></a>
  <a href="https://twitter.com/slletshow"><i class="svg-icon twitter"></i></a>
  <a href="mailto:justkiddinshow@gmail.com"><i class="svg-icon email"></i></a>-->
</div>
<div class="posts">
  {% for post in site.categories['totalknockout'] %}
    {% unless post.hidden == true %}
    <article style="padding: 1em;" class="post">
    {% if post.artwork <> Null %}
      <div style="display: grid; grid-template-columns: repeat(3, minmax(0, 1fr)); text-align: center; grid-gap: 1rem; margin:15px 0">
        <div style="display: flex; flex-direction: column; height: 100%; justify-content: center; align-items: center;"><img style="vertical-align:middle; max-width:200px; width:100%" src="{{post.artwork}}"></div>
        <div style="grid-column-start: 2; grid-column-end: 4; display: flex; flex-direction: column; height: 100%; justify-content: center;">
      {% endif %}
      <a href="{{ site.baseurl }}{{ post.url }}">
          {% assign titlelc = post.title | downcase %}
          {% assign showlc = post.show | downcase %}
          <h1 style="margin: 0;">{% unless post.season == Null %}Season {{ post.season }}{% endunless %}{% unless post.season == Null or post.episode == Null and titlelc == showlc %}: {% endunless %}{% unless post.episode == Null %}#{{ post.episode }}{% endunless %}{% unless post.episode == Null or titlelc == showlc %} - {% endunless %}{% unless titlelc == showlc %}{{ post.title }}{% endunless %}</h1><div>
          <p class="post_date">{{ post.date | date: "%e %B %Y" }}</p>
        </div>
      </a>
      {% if post.elsewhere %}<p style="text-align: center;">🔀 from {{post.elsewhere}}</p>{% endif %}
      {% if post.artwork <> Null %}
      </div>
      </div>
      {% endif %}
      <div style="text-align:center">{% if post.mp3 != Null %}
      <audio controls style="width: 75%; margin-top: 15px;">
        <source src="{{ post.mp3 }}" type="audio/mpeg"/>
        Your browser does not support the audio element.
      </audio>
      {% else %}{{ post.excerpt }}{% endif %}</div>
      <a href="{{ site.baseurl }}{{ post.url }}" class="read-more">Show Notes</a>
    </article>
    {% endunless %}
  {% endfor %}
</div>
