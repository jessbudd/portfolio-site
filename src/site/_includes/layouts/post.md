---
layout: layouts/base.njk
pageClass: posts
templateEngineOverride: njk, md
---

<p class="date">
  Posted <time datetime="{{ date }}">{{ date | dateDisplay }}</time>
</p>
<main>

  {{ content | safe }}

  <div class="bio">
    <p>
      Jess Budd is a digital producer at <a href="https://hbf.com.au">HBF</a>, a UI developer and a web accessibility consultant.  She is a co-organiser of <a href="https://fenders.co/">Fenders Perth</a> and is often found volunteering her time mentoring women learning to code. She’s known for her love of cheese, but is also crazy about UX design, technology, futurism and doggos.
    </p>
  </div>
</main>
