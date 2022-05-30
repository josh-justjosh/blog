---
layout: page
permalink: /archive
title: Posts Archive
---


<div id="archives">
  <section id="archive">
    {%for post in site.posts %}
    {% assign titlelc = post.title | downcase %}
    {% assign showlc = post.show | downcase %}
    {% if forloop.first == true %}
    <h2 id="{{ post.date | date: '%Y' }}" style="text-align:left;">{{ post.date | date: '%Y' }}</h2>
    <ul>
      <h3 id="{{ post.date | date: '%Y%m' }}" style="text-align:left;">{{ post.date | date: '%B %Y' }}</h3>
      <ul>
        <h4 id="{{ post.date | date: '%Y%m%e' }}" style="text-align:left;">{{ post.date | date: '%e %B %Y' }}</h4>
        <ul>
          <div style="display:flex; flex-wrap: wrap;"><li style="flex-grow:1; margin: auto 0 auto;"><b><a href="{{ site.baseurl }}{{ post.url }}">{% if post.title and post.title != "" %}{% if post.categories contains "podcast" %}{{ post.show }}: {% unless post.season == Null %}Season {{ post.season }}{% endunless %}{% unless post.season == Null or post.episode == Null and titlelc == showlc %}: {% endunless %}{% unless post.episode == Null %}#{{ post.episode }}{% endunless %}{% unless post.episode == Null or titlelc == showlc %} - {% endunless %}{% unless titlelc == showlc %}{{ post.title }}{% endunless %}{% elsif post.categories contains "parkrun" %}parkrun #{{ post.number }}: {{ post.location }}{% unless post.locnumber == 1 %} #{{ post.locnumber }}{% endunless %}{% else %}{{post.title}}{% endif %}{% else %}{{post.excerpt |strip_html}}{%endif%}</a></b></li>{% if post.published == false %}<div class="post-unpublished" style="margin:0;flex-grow:1"><p style="margin:1px 0 1px auto; width:min-content; text-align:end;">Unpublished</p></div>{% elsif post.hidden == true %}<div class="post-unpublished" style="margin:0;flex-grow:1"><p style="margin:1px 0 1px auto; width:min-content; text-align:end;">Hidden</p></div>{% endif %}</div>
          {% endif %}
          {% unless post.next %}
          {% else %}
          {% capture day %}{{ post.date | date: '%e %B %Y' }}{% endcapture %}
          {% capture nday %}{{ post.next.date | date: '%e %B %Y' }}{% endcapture %}
          {% capture month %}{{ post.date | date: '%B %Y' }}{% endcapture %}
          {% capture nmonth %}{{ post.next.date | date: '%B %Y' }}{% endcapture %}
          {% capture year %}{{ post.date | date: '%Y' }}{% endcapture %}
          {% capture nyear %}{{ post.next.date | date: '%Y' }}{% endcapture %}
          {% if year != nyear %}
        </ul>
      </ul>
    </ul>
    <h2 id="{{ post.date | date: '%Y' }}" style="text-align:left;">{{ post.date | date: '%Y' }}</h2>
    <ul>
      <h3 id="{{ post.date | date: '%Y%m' }}" style="text-align:left;">{{ post.date | date: '%B %Y' }}</h3>
      <ul>
        <h4 id="{{ post.date | date: '%Y%m%e' }}" style="text-align:left;">{{ post.date | date: '%e %B %Y' }}</h4>
        <ul>
        {% elsif month != nmonth %}
        </ul>
      </ul>
      <h3 id="{{ post.date | date: '%Y%m' }}" style="text-align:left;">{{ post.date | date: '%B %Y' }}</h3>
      <ul>
      <h4 id="{{ post.date | date: '%Y%m%e' }}" style="text-align:left;">{{ post.date | date: '%e %B %Y' }}</h4>
      <ul>
      {% elsif day != nday %}
    </ul>
    <h4 id="{{ post.date | date: '%Y%m%e' }}" style="text-align:left;">{{ post.date | date: '%e %B %Y' }}</h4>
    <ul>
    {% endif %}
    {% unless post.hidden == true %}
    <div style="display:flex; flex-wrap: wrap;"><li style="flex-grow:1; margin: auto 0 auto;"><b><a href="{{ site.baseurl }}{{ post.url }}">{% if post.title and post.title != "" %}{% if post.categories contains "podcast" %}{{ post.show }}: {% unless post.season == Null %}Season {{ post.season }}{% endunless %}{% unless post.season == Null or post.episode == Null and titlelc == showlc %}: {% endunless %}{% unless post.episode == Null %}#{{ post.episode }}{% endunless %}{% unless post.episode == Null or titlelc == showlc %} - {% endunless %}{% unless titlelc == showlc %}{{ post.title }}{% endunless %}{% elsif post.categories contains "parkrun" %}parkrun #{{ post.number }}: {{ post.location }}{% unless post.locnumber == 1 %} #{{ post.locnumber }}{% endunless %}{% else %}{{post.title}}{% endif %}{% else %}{{post.excerpt |strip_html}}{%endif%}</a></b></li>{% if post.published == false %}<div class="post-unpublished" style="margin:0;flex-grow:1"><p style="margin:1px 0 1px auto; width:min-content; text-align:end;">Unpublished</p></div>{% elsif post.hidden == true %}<div class="post-unpublished" style="margin:0;flex-grow:1"><p style="margin:1px 0 1px auto; width:min-content; text-align:end;">Hidden</p></div>{% endif %}</div>
    {% endunless %}
    {% endunless %}
    {% endfor %}
    </ul>
    </ul>
    </ul>
  </section>
</div>
