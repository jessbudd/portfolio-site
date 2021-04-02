---
title: Blog
layout: layouts/base.njk
subtitle: Read some of my musings on web development, digital accessibility, technology, learning...
---

<div class="container__blog">
  <h1 class="center">{{ title }}</h1>
  <!-- {%- if subtitle %}<p class="subtitle">{{ subtitle | safe }}</p>{% endif %} -->
  
  <p class="center">
    <span class="post__tag"><a href="/post">Post</a></span>
    <span class="post__tag"><a href="/blog/dev">dev</a></span>
    <span class="post__tag"><a href="/blog/a11y">a11y</a></span>
    <span class="post__tag"><a href="/blog/life">life</a></span>
    <span class="post__tag"><a href="/blog/speaking">speaking</a></span>
  </p>

  <ul class="listing">
  {%- for post in collections.post | reverse -%}
    {% include "blog-repeat.njk" %}
  {%- endfor -%}

  </ul>

</div>
