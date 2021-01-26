---
title: gallery
# subtitle:
layout: layouts/blank.njk
date: 2021-12-12
meta:
excerpt:
# tags: funstuff, exercises
# img: https://jessbudd.com/images/featured/---.png
draft: true
---

<h1>{{ title }}</h1>

{%- if subtitle %}<p class='subtitle'>{{ subtitle | safe }}</p>{% endif %}

<div class="galleries">
<div class="gallery gallery1">
    <img src="../../images/TNF-fanorak.png" alt="Photo 1" tabindex="0" title="This is the title of the image"
    data-description="This is the description of the image">
        <img src="../../images/270-camo-sunset.jpg" alt="Photo 1" tabindex="0" title="This is the title of the image"
    data-description="This is the description of the image">
    <img src="../../images/canada-goose.jpg" alt="Photo 1" tabindex="0" title="This is the title of the image"
    data-description="This is the description of the image">
    <img src="../../images/coral-yeti.jpg" alt="Photo 1" tabindex="0" title="This is the title of the image"
    data-description="This is the description of the image">
        <img src="../../images/270-camo-sunset.jpg" alt="Photo 1" tabindex="0" title="This is the title of the image"
    data-description="This is the description of the image">
    <img src="../../images/canada-goose.jpg" alt="Photo 1" tabindex="0" title="This is the title of the image"
    data-description="This is the description of the image">
    <img src="../../images/coral-yeti.jpg" alt="Photo 1" tabindex="0" title="This is the title of the image"
    data-description="This is the description of the image">
    <img src="../../images/TNF-fanorak.png" alt="Photo 1" tabindex="0" title="This is the title of the image"
    data-description="This is the description of the image">
</div>

<div class="gallery gallery2">
    <img src="../../images/270-camo-sunset.jpg" alt="Photo 1" tabindex="0" title="This is the title of the image"
    data-description="This is the description of the image">
    <img src="../../images/canada-goose.jpg" alt="Photo 1" tabindex="0" title="This is the title of the image"
    data-description="This is the description of the image">
    <img src="../../images/coral-yeti.jpg" alt="Photo 1" tabindex="0" title="This is the title of the image"
    data-description="This is the description of the image">
    <img src="../../images/TNF-fanorak.png" alt="Photo 1" tabindex="0" title="This is the title of the image"
    data-description="This is the description of the image">
        <img src="../../images/270-camo-sunset.jpg" alt="Photo 1" tabindex="0" title="This is the title of the image"
    data-description="This is the description of the image">
    <img src="../../images/canada-goose.jpg" alt="Photo 1" tabindex="0" title="This is the title of the image"
    data-description="This is the description of the image">
    <img src="../../images/coral-yeti.jpg" alt="Photo 1" tabindex="0" title="This is the title of the image"
    data-description="This is the description of the image">
    <img src="../../images/TNF-fanorak.png" alt="Photo 1" tabindex="0" title="This is the title of the image"
    data-description="This is the description of the image">
</div>

<div class="modal">
    <div class="modalInner">
    <button aria-label="Previous Photo" class="prev">←</button>
    <figure>
        <img src="../../images/TNF-fanorak.png">
        <figcaption>
        <h2>Test Title</h2>
        <p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Dolor dignissimos obcaecati nisi placeat eaque
            voluptate, exercitationem eius? Non, iusto provident itaque, voluptate labore a alias officia, amet sunt
            pariatur praesentium tenetur voluptatibus dolores mollitia quasi aliquid assumenda possimus maiores
            exercitationem!</p>
        </figcaption>
    </figure>
    <button class="next" aria-label="Next Photo">→</button>
    </div>
</div>
</div>

<script>
function Gallery(gallery) {
    if (!gallery) {
        throw new Error('No Gallery found');
    }
    console.log(gallery);

    const images = Array.from(gallery.querySelectorAll('img'));
    console.log(images);
}

const gallery1 = Gallery(document.querySelector('.gallery1'));
const gallery2 = Gallery(document.querySelector('.gallery2'));



</script>

<style>
body {
  min-height: 100vh;
  display: grid;
  align-items: start;
  justify-items: center;
}

.galleries {
  padding: 2rem;
  display: grid;
  grid-template-columns: 1fr;
  grid-gap: 2rem;
}
.gallery {
    display: grid;
    width: 100%;
    grid-template-columns: repeat(auto-fill, minmax(150px, 1fr));
    grid-gap: 20px;
    align-items: stretch;
    background: white;
    padding: 2rem;
    }

    .gallery img {
      width: 100%;
      object-fit: cover;
      border:1px solid black;
    }

    .modal {
      position: fixed;
      background: rgba(0, 0, 0, 0.5);
      z-index: 2;
      top: 0;
      right: 0;
      bottom: 0;
      left: 0;
      display: grid;
      align-items: center;
      justify-items: center;
      pointer-events: none;
      opacity: 0;
      transition: opacity 0.5s;
    }

    .modalInner {
      border-radius: 4px;
      background: white;
      box-shadow: 0 0 10px 10px rgba(0, 0, 0, 0.05);
      transform: translateY(-100vh);
      transition: all 0.5s;
      max-width: 1000px;
      height: calc(100vh - 100px);
      display: grid;
      grid-template-columns: 50px 1fr 50px;
      color: black;
      margin: 3rem;
    }

    .modal figure {
      height: 100%;
      display: grid;
      margin: 0;
      grid-template-rows: 1fr auto;
    }

    .modal img {
      height: 100%;
      width: 100%;
      object-fit: contain;
    }

    .modal.open {
      opacity: 1;
      pointer-events: all;
    }

    .modal figcaption {
      padding: 10px;
    }

    .modal h2 {
      color: black;
    }

    .modal.open .modalInner {
      transform: translateY(0);
    }
</style>
