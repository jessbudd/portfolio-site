---
title: Fun Stuff
layout: layouts/base.njk
subtitle: A compilation of little things I'm making for fun
---

<div class="container__blog">
  <!-- <h1>{{ title }}</h1>
  {%- if subtitle %}<p class="subtitle">{{ subtitle | safe }}</p>{% endif %} -->

<ul class="listing">
{%- for page in collections.funstuff | reverse -%}
  <li >
    <time datetime="{{ page.date }}">{{ page.date | dateDisplay(" d LLLL  y") }}</time>
    <h2 class="h3 archive__title"><a href="{{ page.url }}">{{ page.data.title }}</a></h2>
    {%- if page.data.excerpt %}<p> {{ page.data.excerpt }}</p>{% endif %}
    <a href="{{ page.url }}" aria-label="View - {{ page.data.title }}" class="archive__read-more">View</a>
  </li>
{%- endfor -%}
</ul>

</div>
