---
layout: archive
permalink: /stat/
title: "Statistics"
author_profile: true
header:
  image: "/images/RL_TheRoad_03.jpg"
---

{% assign postsStat = site.posts | where: "categories","Stat" %}
{% assign posts = postsStat | sort: "order" %}
<ul>
  {% for post in posts %}
    {% unless post.next %}
      <font color="#778899"><h2>{{ post.date | date: '%Y %b' }}</h2></font>
    {% else %}
      {% capture year %}{{ post.date | date: '%Y %b' }}{% endcapture %}
      {% capture nyear %}{{ post.next.date | date: '%Y %b' }}{% endcapture %}
      {% if year != nyear %}
        <font color="#778899"><h2>{{ post.date | date: '%Y %b' }}</h2></font>
      {% endif %}

    {% endunless %}
   {% include archive-single.html %}
  {% endfor %}
</ul>
