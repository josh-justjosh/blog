---
layout: page
permalink: /archive/
title: Archive
---


<div id="archives">
  <section id="archive">
      {%for post in site.posts %}
      <ul class="this">
          {% else %}
          {% capture month %}{{ post.date | date: '%B %Y' }}{% endcapture %}
          {% capture nmonth %}{{ post.next.date | date: '%B %Y' }}{% endcapture %}
          {% if month != nmonth %}
      </ul>
      <h3>{{ post.date | date: '%B %Y' }}</h3>
      <ul class="past">
          {% endif %}
          <p><center><b><a href="{{ site.baseurl }}{{ post.url }}">{% if post.title and post.title != "" %}{{post.title}}{% else %}{{post.excerpt |strip_html}}{%endif%}</a></b> - {% if post.date and post.date != "" %}{{ post.date | date: "%e %B %Y" }}{%endif%}</center></p>
          {% endfor %}
      </ul>
  </section>
</div>
