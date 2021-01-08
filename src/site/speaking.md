---
title: Speaking
layout: layouts/base.njk
# subtitle: I like to talk about front end devs accessibility and front-end development at a range of conferences and events.
meta: A list of Jess Budd's upcoming and past tech talks.
---

<div class="container__blog talks">
  <h1>{{title}}</h1>

{%- if subtitle %}<p class="subtitle">{{ subtitle | safe }}</p>{% endif %}

  <hr>

{% include "upcoming-talks.njk" %}

<hr>

<h2 id="pastTalks"> Previous Talks</h2>

### [LaraconAU](https://laracon.com.au/) &nbsp;

Sydney, 2019 - <a href="https://noti.st/jessbudd/pQ4gBc/" class="talk__link"> View Talk</a></p>

<figure>
<iframe width="950" height="615" src="https://www.youtube.com/embed/wv9y341Vpdg" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
<p class="talk__title">Making Single Page Apps Accessible</p>
</figure>

### [Google DevFest](https://www.gdgmelbourne.com/devfest) &nbsp;

Melbourne, 2019 - <a href="https://noti.st/jessbudd/sB6Kmd" class="talk__link"> View Talk</a></p>

<figure>
<iframe width="950" height="615" src="https://www.youtube.com/embed/C7B-HkapCr8" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
<figcaption class="talk__title">
<p>Live Life in Beta: What Software Development Can Teach Us About Life </p>
</figcaption>

</figure>

### [DDDAdelaide](https://www.dddadelaide.com/) &nbsp;

Adelaide, 2019 - <a href="https://bit.ly/DDDA19" class="talk__link"> View Talk</a></p>

<figure>
<p data-notist="jessbudd/UUp8f2">View <a href="https://noti.st/jessbudd/UUp8f2">Making React Apps Accessible: It’s easier than you think</a> on Notist.</p><script async src="https://on.notist.cloud/embed/002.js"></script>
<figcaption class="talk__title">
<p>Making React Apps Accessible: It's easier than you think</p>
</figcaption>

</figure>

<!-- <figure>
  <img src="/images/speakingLaracon2.jpg" alt="Jess Budd speaking at LarconAU">

<figcaption>Presenting at LaraconAU 2019. Photo credit: Giles Park</figcaption>
</figure> -->
</div>
<style>
  .talks h3 {
    margin-top: 60px;
  }
  iframe {
    max-width: 100%;
  }
</style>
