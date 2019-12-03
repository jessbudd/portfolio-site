---
title: Fun Stuff
layout: layouts/base.njk
subtitle: Little things I'm making for fun!
---

<div class="container__blog">
  <h1>{{ title }}</h1>
  {%- if subtitle %}<p class="subtitle">{{ subtitle | safe }}</p>{% endif %}

<ul class="listing">
{%- for page in collections.funstuff | reverse -%}
  <li>
    <a href="{{ page.url }}">{{ page.data.title }}</a> -
    <time datetime="{{ page.date }}">{{ page.date | dateDisplay("LLLL  y") }}</time>
  </li>
{%- endfor -%}
</ul>

</div>
