---
title: Etch-a-sketch
layout: layouts/blank.njk
date: 2020-12-20
meta: Etch-a-sketch, JavaScript practice
tags: funstuff
# img: https://jessbudd.com/images/featured/quoteGenerator.png
# excerpt: A simple quiz to see if you were a first generation pokemon, which pokemon would you be? Made on a lazy Sunday afternoon for my 6 and 9 year olds.
---

<div class="fun-stuff">
<h1>{{title}}</h1>
<div class="canvasWrap">
    <canvas width="1600" height="1000" id="etch-a-sketch"></canvas>
    <div class="buttons">
      <button class="shake">Clear!</button>
    </div>

  </div>
</div>

<script>
const canvas = document.querySelector('#etch-a-sketch');
const ctx = canvas.getContext(`2d`);
const shakeButton = document.querySelector('.shake');

const {width, height } = canvas

let x = Math.floor(Math.random() * width);
let y = Math.floor(Math.random() * height);

ctx.lineJoin = 'round';
ctx.lineCap = 'round';
ctx.lineWidth = 10;

ctx.beginPath();
ctx.moveTo(x,y);
ctx.lineTo(x,y)
ctx.stroke();
// console.log(canvas,ctx, shakeButton);

function draw(key) {
    console.log(key);
}


function handleKey(e) {
    if (e.key.includes('Arrow')) {

    e.preventDefault();
    draw({ key: e.key });
    // console.log(e.key);
    }
}

window.addEventListener('keydown', handleKey);

</script>

<style>
/* fun stuff styles */

.fun-stuff {
  text-align: center;
  max-width: 900px;
  margin: 80px auto 5px;
}
.quote__wrapper {
    min-height: 300px;
    padding-top: 72px;
}
body {
      min-height: 100vh;
      display: grid;
      align-items: center;
      justify-items: center;
    }
.shake {
    text-decoration: none;
    background-color: transparent;
    color: #00ffd2;
    border: #00ffd2 1px solid;
    font-size: 1.2rem;
    padding: 12px 24px;
    border-radius: 4px;
    cursor: pointer;
}
canvas {
    border: 30px solid #cec2ef;
    margin: 20px 0;
    border-radius: 10px;
    /* Set the width and height to half the actual size so it doesn't look pixelated */
    width: 800px;
    height: 500px;
    background: white;
}

canvas.shake {
    animation: shake 0.5s linear 1;
}

@keyframes shake {

    10%,
    90% {
    transform: translate3d(-1px, 0, 0);
    }

    20%,
    80% {
    transform: translate3d(2px, 0, 0);
    }

    30%,
    50%,
    70% {
    transform: translate3d(-4px, 0, 0);
    }

    40%,
    60% {
    transform: translate3d(4px, 0, 0);
    }
}
</style>
