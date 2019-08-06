---
layout: archive
permalink: /python-snippets/
title: "Python snippets"
author_profile: true
header:
  image: "/images/butterlfy_01.jpg"
---

<ul>
  {% for page in site.snippets %}
    {% unless page.next %}
      <font color="#778899"><h2>{{ page.date | date: '%Y %b' }}</h2></font>
    {% else %}
      {% capture year %}{{ page.date | date: '%Y %b' }}{% endcapture %}
      {% capture nyear %}{{ page.next.date | date: '%Y %b' }}{% endcapture %}
      {% if year != nyear %}
        <font color="#778899"><h2>{{ page.date | date: '%Y %b' }}</h2></font>
      {% endif %}

    {% endunless %}
   {% include archive-single.html %}
  {% endfor %}
</ul>
