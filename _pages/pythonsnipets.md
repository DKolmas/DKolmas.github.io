---
layout: archive
permalink: /python-snippets/
title: "Python snippets"
author_profile: true
header:
  image: "/images/butterlfy_01.jpg"
---

<ul>
  {% assign sorted-post = site.posts | where: "categories","PySnippet" %}
  {% for post in sorted-posts limit: 5 %}
    {{post.title}}
  {% endfor %}
</ul>
