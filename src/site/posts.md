---
title: Blog
layout: layouts/base.njk
subtitle: Read some of my musings on web development, digital accessibility, technology, learning...
---

<div class="container__blog">
  <!-- <h1>{{ title }}</h1> -->
  <!-- {%- if subtitle %}<p class="subtitle">{{ subtitle | safe }}</p>{% endif %} -->

<ul class="listing">
{%- for page in collections.post | reverse -%}
  <li>
    <time datetime="{{ page.date }}">{{ page.date | dateDisplay(" d LLLL  y") }}</time>
    <h2 class="h3 archive__title"><a href="{{ page.url }}">{{ page.data.title }}</a></h2> 

    
  <a href="">Read more</a>

<hr>
  </li>

{%- endfor -%}
</ul>

</div>
