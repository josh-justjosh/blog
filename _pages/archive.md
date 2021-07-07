---
layout: page
permalink: /archive
title: Posts Archive
date: 2021-12-31
---


<div id="archives">
  <section id="archive">
     <h3 style="text-align:left;">Most Recent Posts</h3>
      {%for post in site.posts %}
      {% unless post.next %}
      <ul class="this">
          {% else %}
          {% capture month %}{{ post.date | date: '%B %Y' }}{% endcapture %}
          {% capture nmonth %}{{ post.next.date | date: '%B %Y' }}{% endcapture %}
          {% capture year %}{{ post.date | date: '%Y' }}{% endcapture %}
          {% capture nyear %}{{ post.next.date | date: '%Y' }}{% endcapture %}
          {% if year != nyear %}
      </ul>
      <h2 id="{{ post.date | date: '%Y' }}" style="text-align:left;">{{ post.date | date: '%Y' }}</h2>
      <ul class="past">
          {% endif %}
          {% if month != nmonth %}
          <h3 id="{{ post.date | date: '%Y%m' }}" style="text-align:left;">{{ post.date | date: '%B %Y' }}</h3>
          {% endif %}
          {% unless post.hidden == true %}
          <div style="display:flex; flex-wrap: wrap;"><li style="flex-grow:1; margin: auto 0 auto;"><b><a href="{{ site.baseurl }}{{ post.url }}">{% if post.title and post.title != "" %}{{post.title}}{% else %}{{post.excerpt |strip_html}}{%endif%}</a></b> - {% if post.date and post.date != "" %}{{ post.date | date: "%e %B %Y" }}{%endif%}</li>{% if post.published == false %}<div class="post-unpublished" style="margin:0;flex-grow:1"><p style="margin:1px 0 1px auto; width:min-content; text-align:end;">Unpublished</p></div>{% elsif post.hidden == true %}<div class="post-unpublished" style="margin:0;flex-grow:1"><p style="margin:1px 0 1px auto; width:min-content; text-align:end;">Hidden</p></div>{% endif %}</div>
          {% endunless %}
          {% endunless %}
          {% endfor %}
      </ul>
    <h3 style="text-align:left;">Oldest Posts</h3>
  </section>
</div>
