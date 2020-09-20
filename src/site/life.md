---
title: Life
layout: layouts/base.njk
# subtitle: A compilation of little things I'm making for fun.
---

<div class="container__blog">
  <h1>{{ title }}</h1>
  {%- if subtitle %}<p class="subtitle">{{ subtitle | safe }}</p>{% endif %}
 

<ul class="listing">
{%- for post in collections.life | reverse -%}
  {% include "blog-repeat.njk" %}
{%- endfor -%}
</ul>

</div>
