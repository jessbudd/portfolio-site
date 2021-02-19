---
title: Speaking
layout: layouts/base.njk
# subtitle: Posts about community, mentoring, speaking etc
---

<div class="container__blog">
  <h1>{{ title }}</h1>
  {%- if subtitle %}<p class="subtitle">{{ subtitle | safe }}</p>{% endif %}

<ul class="listing">
{%- for post in collections.speaking | reverse -%}
  {% include "blog-repeat.njk" %}
{%- endfor -%}
</ul>

</div>
