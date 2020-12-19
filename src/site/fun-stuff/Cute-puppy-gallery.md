---
title: Cute puppy gallery
layout: layouts/blank.njk
date: 2020-12-19
meta: Cute puppy gallery
# tags: funstuff
# img: https://jessbudd.com/images/featured/quoteGenerator.png
excerpt: Need a quick pick-me-up? Cute puppers and floofers and doggos waiting for you in here.
---

<h1>{{title}}</h1>

<div class="list">
    <div class="card" data-description="test" >
        <img src="https://picsum.photos/200?random=1" alt="">
            <h2 class="name">Lorem Ipsum</h2>
            <button class="btn">View larger</button>
    </div>
    <div class="card" data-description="test2" >
        <img src="https://picsum.photos/200?random=2"alt="">
            <h2 class="name">Lorem Ipsum</h2>
            <button class="btn">View larger</button>
    </div>
    <div class="card" data-description="test3" >
        <img src="https://picsum.photos/200?random=3" alt="">
            <h2 class="name">Lorem Ipsum</h2>
            <button class="btn">View larger</button>
            </div>
    <div class="card" data-description="test4" >
        <img src="https://picsum.photos/200?random=4" alt="">
            <h2 class="name">Lorem Ipsum</h2>
            <button class="btn">View larger</button>
    </div>   
</div>
<!-- <button class="btn">Load more floofers</button> -->
<div class="modal-outer">
    <div class="modal-inner">
        <h2 class="title">title and text and stuff</h2>
    </div>
</div>

<script>

const cardButtons = document.querySelectorAll('.btn');
const modalOuter = document.querySelector('.modal-outer');
const modalInner = document.querySelector('.modal-inner');

function handleButtonClick(e) {
    const button = e.currentTarget;
    const card = button.closest('.card');
    const name = card.querySelector('h2').textContent;
    const imgSrc =  card.querySelector('img').src;
    const desc = card.dataset.description;

    modalInner.innerHTML = 
    `<img src="${imgSrc.replace('200', '600')}" alt="${name}">
    <p>${desc}</p>`
    ;
    modalOuter.classList.add('open');
}

function closeModal() {
    modalOuter.classList.remove('open');
}

modalOuter.addEventListener('click', function(e) {
    if( e.target === modalOuter) {
        closeModal();
    }
})

cardButtons.forEach(button => button.addEventListener('click', handleButtonClick))

 // stop people scrolling while modal is open 

</script>

<style>

    .modal-outer {
        display: grid;
        height: 100vh;
        width: 100vw;
        top: 0;
        left: 0;
        background: rgba(0,0,0,.5);
        position: absolute;
        pointer-events: none;
        justify-content: center;
        align-items: center;
        opacity: 0;
        transition: opacity .2s;
    }
    .modal-outer.open {
        opacity: 1;
        pointer-events: all;
    }
    .modal-inner {
        background: #fff;
        padding: 20px;
        position: relative;
        width: 620px;
        max-width: 100%;
        max-width: 600px;
        min-height: 200px;
        border-radius: 4px;
    }
    p {
        color: #666;

    }
body {
    min-height: 100vh;
    display: grid;
    align-items: center;
    justify-items: center;
}
.container {
  text-align: center;
  margin: 2% auto 0;
}
.list {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(150px, 1fr));
    grid-gap: 40px;
    margin-top: 40px;
}
.list .card {
    border-radius: 4px;
    padding: 10px;
}
img {
    width: 100%;
    border-radius: 4px 4px 0 0;
}
.name {
    margin: 12px 0;
    color: #583ca0;
    font-size: 1.2em;
}

.btn {
    text-decoration: none;
    background-color: transparent;
    color: #00ffd2;
    border: #00ffd2 1px solid;
    font-size: 1.2rem;
    padding: 12px 24px;
    border-radius: 4px;
    cursor: pointer;
    margin-top: 10px;
}
.card .btn {
    color: #583ca0;
    border: #583ca0 1px solid;
    font-size: 1rem;

}

</style>
