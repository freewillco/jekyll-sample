---
layout: page
title: "Locations"
permalink: "/locations/"
---

<ul>
  {% for location in site.locations %}
    <li>
      <a href="{{ location.id }}">{{ location.name }}</a>
    </li>
  {% endfor %}
</ul>