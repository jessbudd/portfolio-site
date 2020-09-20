---
title: Blog
layout: layouts/base.njk
subtitle: Read some of my musings on web development, digital accessibility, technology, learning...
---

<div class="container__blog">
  <h1 class="sr-only">{{ title }}</h1>
  <!-- {%- if subtitle %}<p class="subtitle">{{ subtitle | safe }}</p>{% endif %} -->

<ul class="listing">
{%- for page in collections.post | reverse -%}
  {% include "blog-repeat.njk" %}
{%- endfor -%}

</ul>

</div>
