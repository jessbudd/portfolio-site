---
title: Speaking
layout: layouts/base.njk
subtitle: I love to share my knowledge about web accessibility and front-end development with the tech community. This year I'm doing this through public speaking. <br>See my upcoming and past talk events below.
meta: A list of Jess Budd's upcoming and past tech talks.
---
<div class="container__blog talks">
  <h1>{{title}}</h1>
  {%- if subtitle %}<p class="subtitle">{{ subtitle | safe }}</p>{% endif %}

  <hr>

{% include "upcoming-talks.njk" %}

<hr>

## Past Talks

<p class="subtitle">Coming soon</p>


<!-- ### [LaraconAU](https://laracon.com.au/)

<p class="talk__title">Making React Apps Accessible: It's easier than you think | <a href="#" class="talk__link">View Talk</a></p>

<p class="talk__details">31 October - 1 November 2019, Sydney Australia</p> -->

</div>
