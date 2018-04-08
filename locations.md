---
layout: page
title: Locations
---

<ul>
  {% for location in site.locations %}
    <li>
      <a href="{{ location.url }}">{{ location.title }}</a>
    </li>
  {% endfor %}
</ul>