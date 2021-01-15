---
layout: page
permalink: /archive
title: Archive
---


<div id="archives">
  <section id="archive">
      <h3>This year's posts</h3>
      {%for post in site.posts %}
      {% unless post.next %}
      <ul class="this">
          {% else %}
          {% capture year %}{{ post.date | date: '%Y' }}{% endcapture %}
          {% capture nyear %}{{ post.next.date | date: '%Y' }}{% endcapture %}
          {% if year != nyear %}
      </ul>
      <h3>{{ post.date | date: '%Y' }}</h3>
      <ul class="past">
          {% endif %}
          {% endunless %}
          <p><center><b><a href="{{ site.baseurl }}{{ post.url }}">{% if post.title and post.title != "" %}{{post.title}}{% else %}{{post.excerpt |strip_html}}{%endif%}</a></b> - {% if post.date and post.date != "" %}{{ post.date | date: "%e %B %Y" }}{%endif%}</center></p>
          {% endfor %}
      </ul>
  </section>
</div>
