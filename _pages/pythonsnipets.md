---
layout: archive
permalink: /python-snippets/
title: "Python snippets"
author_profile: true
header:
  image: "/images/butterlfy_01.jpg"
---

{% assign posts = site.posts | where: "categories","PySnippet" %}
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
