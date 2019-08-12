---
layout: layouts/base.njk
pageClass: posts
templateEngineOverride: njk, md
---

<div class="container__blog">
  <h1>{{ title }}</h1>
  {%- if subtitle %}<p class="subtitle">{{ subtitle | safe }}</p>{% endif %}
  
<p class="date">
  Posted <time datetime="{{ date }}">{{ date | dateDisplay }}</time>
</p>
<main>



  {{ content | safe }}

  <div class="bio">
    <img src="/images/jess-budd-bio-fun.jpg" class="bio__avatar" alt="Jess Budd informal headshot" />
    <p class="bio__text">
      <!-- Jess Budd is a digital producer at <a href="https://hbf.com.au">HBF</a>, a freelance UI developer and web accessibility consultant.  She is a co-organiser of <a href="https://fenders.co/">Fenders Perth</a> and is often found volunteering her time mentoring women learning to code. She’s known for her love of cheese, but is also crazy about UX design, technology, futurism and doggos. -->
      Jess Budd is a UI developer, accessibility consultant and digital producer. She co-organises a <a href="https://fenders.co/">meetup group for front-end developers</a>, mentors women learning to code and has a love of cheese, technology and doggos.  
    </p>
  </div>
</main>
</div>
