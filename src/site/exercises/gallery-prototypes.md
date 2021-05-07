---
title: Gallery with Prototypes
# subtitle:
layout: layouts/blank.njk
date: 2021-01-27
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

    this.gallery = gallery;

    this.images = Array.from(gallery.querySelectorAll('img'));
    this.modal = document.querySelector('.modal');
    
    this.prevButton = this.modal.querySelector('.prev');
    this.nextButton = this.modal.querySelector('.next');

    // bind our methods to the instance when we need them
    this.showNextImage = this.showNextImage.bind(this);
    this.showPrevImage = this.showPrevImage.bind(this);
    this.handleKeyUp = this.handleKeyUp.bind(this);
    this.handleClickOutside = this.handleClickOutside.bind(this);

    this.images.forEach(image => image.addEventListener('click', (e) => this.showImage(e.currentTarget)));

    this.images.forEach(image => image.addEventListener('keyup', (e) => {
        if (e.key === 'Enter') {
            this.showImage(e.currentTarget);
        }
    }))
    this.modal.addEventListener('click', this.handleClickOutside);
}

Gallery.prototype.openModal = function() {
        // check if this.modal is already open
        if (this.modal.matches('.open')) {
            console.info('Modal already open');
            return;
        } 
        this.modal.classList.add('open');

        // event listeners to be bound when we open the this.modal
        window.addEventListener('keyup', this.handleKeyUp);
        this.nextButton.addEventListener('click', this.showNextImage);
        this.prevButton.addEventListener('click', this.showPrevImage);
    }

    Gallery.prototype.closeModal = function() {
        this.modal.classList.remove('open');
        // clean up eventListeners on close
        window.removeEventListener('keyup', this.handleKeyUp);
        this.nextButton.removeEventListener('click', this.showNextImage);
        this.prevButton.removeEventListener('click', this.showPrevImage);
    }

    Gallery.prototype.handleClickOutside = function(e) {
        if (e.target === e.currentTarget) {
            this.closeModal();
        }
    }

    Gallery.prototype.handleKeyUp = function(e) {
        if(e.key === 'Escape') return this.closeModal();
        if(e.key === 'ArrowRight') return this.showNextImage();
        if(e.key === 'ArrowLeft') return this.showPrevImage();
        if(e.key === 'Enter') return this.openModal();
    }

    Gallery.prototype.showImage = function(el) {
        if (!el) {
            console.info(('no image to show'));
        return;
        }
        this.openModal();
        this.modal.querySelector('img').src = el.src;
        this.modal.querySelector('h2').textContent = el.title;
        this.modal.querySelector('p').textContent = el.dataset.description;
        this.currentImage = el;
        // console.log(this.modal, this.currentImage);
    }

    Gallery.prototype.showNextImage = function() {
        this.showImage(this.currentImage.nextElementSibling || this.gallery.firstElementChild);
        
    }    
    Gallery.prototype.showPrevImage = function() {
       this.showImage(this.currentImage.previousElementSibling || this.gallery.lastElementChild);
        
    }

const gallery1 = new Gallery(document.querySelector('.gallery1'));
const gallery2 = new Gallery(document.querySelector('.gallery2'));

console.log(gallery1, gallery2);


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
    button {
        text-decoration: none;
        background-color: #583ca0;
        color: #00ffd2;
        font-size: 1.2rem;
        padding: 12px 24px;
        border-radius: 4px;
        cursor: pointer;
    }
</style>
