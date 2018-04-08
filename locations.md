---
layout: page
title: "Locations"
---

<ul>
  {% for location in site.locations %}
    <li>
      <a href="{{ location.url }}">{{ location.name }}</a>
    </li>
  {% endfor %}
</ul>