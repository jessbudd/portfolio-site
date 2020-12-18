---
title: Etch-a-sketch
layout: layouts/blank.njk
date: 2020-12-10
meta: Etch-a-sketch, JavaScript practice
tags: funstuff
# img: https://jessbudd.com/images/featured/quoteGenerator.png
excerpt: Remeber playing with etch-a-sketchs from when you were a little kid? Like that, but purple and rainbow!
---

<h1>{{title}}</h1>
<div class="canvasWrap">
    <div>
        <canvas width="1600" height="1000" id="etch-a-sketch"></canvas>
    </div>
    <div id="buttons">
        <button class="control btn" name="ArrowLeft">&larr;</button>
        <button class="control btn" name="ArrowUp">&uarr;</button>
        <button class="control btn" name="ArrowRight">&rarr;</button>
        <button class="control btn" name="ArrowDown">&darr;</button>
        <button class="shake btn">Shake</button>
    </div>
</div>

<script>
const canvas = document.querySelector('#etch-a-sketch');
const ctx = canvas.getContext(`2d`);
const shakeButton = document.querySelector('.shake');
const controls = document.querySelectorAll('.control');

// console.log(controls);
const MOVE_AMOUNT = 30;

const {width, height } = canvas


let x = Math.floor(Math.random() * width);
let y = Math.floor(Math.random() * height);

ctx.lineJoin = 'round';
ctx.lineCap = 'round';
ctx.lineWidth = 15;

let hue = 0;
ctx.strokeStyle = `hsl(${hue}, 100%, 50%)`;
ctx.beginPath();
ctx.moveTo(x,y);
ctx.lineTo(x,y)
ctx.stroke();

function draw(key) {
    hue = hue + 1;
    ctx.strokeStyle = `hsl(${hue}, 100%, 50%)`;

    ctx.beginPath();
    ctx.moveTo(x,y);

    switch(key) {
        case 'ArrowUp':
            y = y - MOVE_AMOUNT;
            break;
        case 'ArrowRight':
            x = x + MOVE_AMOUNT;
            break;
        case 'ArrowDown':
            y = y + MOVE_AMOUNT;
            break;
        case 'ArrowLeft':
            x = x - MOVE_AMOUNT;
            break;
        default:
            break;  
    }
    ctx.lineTo(x,y)
    ctx.stroke();
}

function handleClick(e) {
    draw(e.currentTarget.name);

}
function handleKey(e) {
    if (e.key.includes('Arrow')) {
    e.preventDefault();
    draw(e.key );
    }
}

function clearCanvas() {
    canvas.classList.add('shake');
    ctx.clearRect(0, 0, width, height);
    canvas.addEventListener('animationend', function() {
        canvas.classList.remove('shake');
    }, {once : true});
}

window.addEventListener('keydown', handleKey);
shakeButton.addEventListener('click', clearCanvas);
controls.forEach(
    function(control) {
        control.addEventListener('click', handleClick);
    }
);

</script>

<style>
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
.grid-container {
    grid-template-columns: 100%;
}
@media (min-width: 900px) {
    .grid-container {
        grid-template-columns: 70% 10%;
    }
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
canvas {
    border: 30px solid #cec2ef;
    margin: 20px 0;
    border-radius: 10px;
    width: 100%;
    background: white;
    max-width: 800px;
    box-sizing: border-box;
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
