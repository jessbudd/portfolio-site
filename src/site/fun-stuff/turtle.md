---
title: Turtle animation
layout: layouts/blank.njk
date: 2020-12-22
meta: Animation, JavaScript practice
# tags: funstuff
# img: https://jessbudd.com/images/featured/quoteGenerator.png
excerpt: Help Mr Turtle catch the fly with the controls or arrow keys
---

<!-- <h1>{{title}}</h1> -->
<div class="wrapper">
    <div class="buttons">
        <button class="control btn" id="ArrowUp">&uarr;</button>
        <div>
        <button class="control btn" id="ArrowLeft">&larr;</button>
        <button class="control btn" id="ArrowRight">&rarr;</button>
        </div>
        <button class="control btn" id="ArrowDown">&darr;</button>
    </div>
    <img src="/images/funstuff/turtle.png" alt="cartoon turtle" id="turtle" width="150">

<p>Help Mr Turtle catch the fly using arrow keys or buttons.</p>
</div>

<script>
const controls = document.querySelectorAll('.control');
const turtle = document.querySelector('#turtle');
const wrapper = document.querySelector('.wrapper');

const speed = 10;
const MOVE_AMOUNT = 3;

const imgHeight = 30;
let height = window.innerHeight - 60;
let width = window.innerWidth - 60;
let randomHeight = randomPosition((height / 4), height);
let randomWidth = randomPosition((width / 4), width);
let x = 0;
let y = 0;
let flipped = false;
let rotate = 0;

function randomPosition(min, max) {
  min = Math.ceil(min);
  max = Math.floor(max);
  return Math.floor(Math.random() * (max - min) + min); 
  }

window.addEventListener('resize', function() {
    height = window.innerHeight;
    width =  window.innerWidth;
})

function addFlyOnLoad() {
    const fly = document.createElement('img');
    fly.src = "/images/funstuff/fly.png";
    fly.alt = "cartoon fly";
    fly.width =`${imgHeight}`;
    fly.id = "fly";
    fly.style.position = 'absolute';

    fly.style.top = `${randomHeight}px`;
    fly.style.left = `${randomWidth}px`;
    wrapper.appendChild(fly);
}


function resetGame() {
    const fly = document.querySelector('#fly');
    const newRandomHeight = randomPosition((height / 4), height);
    const newRandomWidth = randomPosition((width / 4), width);
    randomHeight = newRandomHeight;
    randomWidth = newRandomWidth;
    fly.style.top = `${newRandomHeight}px`;
    fly.style.left = `${newRandomWidth}px`;

    turtle.setAttribute(`style`, `
        --rotateX: 0;
        --rotate: 0deg;
        --y: 0px;
        --x: 0px;
    `);
    x = 0;
    y = 0;
console.log(turtle);
}

function moveTurtle(command) {

    const isOutOfViewport = function(element) {
        // Get element's bounding
        const bounding = element.getBoundingClientRect();
        // Check if it's out of the viewport on each side
        let out = {};
        out.top = (bounding.top  - 20) < 0;
        out.left = (bounding.left - 20) < 0;
        out.bottom = (bounding.bottom + 20) > window.innerHeight;
        out.right = (bounding.right + 20) > window.innerWidth;
        return out;
    };

    const isOut = isOutOfViewport(turtle);
    let foundFly = false;

    if(command === "ArrowUp" && !isOut.top) {
         y = y - MOVE_AMOUNT;
        rotate = -90; 
    } else if (command === "ArrowRight" && !isOut.right) {
        x = x + MOVE_AMOUNT;
        rotate = 0;
        flipped = false;
    } else if (command === "ArrowDown" && !isOut.bottom) {
        y = y + MOVE_AMOUNT;
        rotate = 90;
    } else if (command === "ArrowLeft" && !isOut.left) {
         x = x - MOVE_AMOUNT;
        rotate = 0;
        flipped = true;
    } else {
        return;
    }

    turtle.setAttribute(`style`, `
    --rotateX: ${flipped ? '180deg' : '0'};
    --rotate: ${rotate}deg;
    --y: ${y * speed}px;
    --x: ${x * speed}px;
    `);
    // make arrow button light up when corresponding arrow key is used
    const arrow = document.querySelector(`#${command}`);
    arrow.focus()

    const turtleLocationX = parseInt(turtle.getBoundingClientRect().x);
    const turtleLocationY = parseInt(turtle.getBoundingClientRect().y);

    const isTurtleOnX = turtleLocationX > (randomWidth - 50) && turtleLocationX < (randomWidth +
    50);
    const isTurtleOnY = turtleLocationY > (randomHeight - 50) && turtleLocationY < (randomHeight + 50);

    if(isTurtleOnX && isTurtleOnY) {
        foundFly = true;
    }

    if (foundFly) {
        foundFly = false;
        alert(`Congratulations! You caught Fly!`);
        resetGame();
    }
}

function handleClick(e) {
    moveTurtle(e.currentTarget.id);

}
function handleKey(e) {
    if (!e.key.includes('Arrow')) return; 
    e.preventDefault();
    moveTurtle(e.key);
} 

window.addEventListener('keydown', handleKey);
controls.forEach(
    function(control) {
        control.addEventListener('click', handleClick);
    }
);


addFlyOnLoad();

</script>

<style>
body {
    min-height: 100vh;
    display: grid;
}
.container {
  margin: 2% auto 0;
}
.wrapper {
    height: 80vh;
    text-align: center;
    position: relative;
    display: grid;
}
.wrapper p {
    color: #cec2ef;
    font-size: .775em;
    align-self: flex-end;
    justify-self: center;
}
.buttons {
    position: absolute;
    top: 0;
    right: 0;
}
#turtle {
    position: relative;
    --x: 0;
    --y: 0;
    --rotateX: 0;
    --rotate: 0;
    transform: translateX(var(--x)) translateY(var(--y)) rotateY(var(--rotateX)) rotate(var(--rotate));
    transition: .2s;
    align-self: flex-start;
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
@media (max-width: 500px) {

.buttons {
    position: absolute;
    top: 0;
    right: 0;
}
#turtle {
    position: relative;
    --x: 0;
    --y: 0;
    --rotateX: 0;
    --rotate: 0;
    transform: translateX(var(--x)) translateY(var(--y)) rotateY(var(--rotateX)) rotate(var(--rotate));
    transition: .2s;
}
#fly {
    width: 20px;
}
#turtle {
    width: 80px;
}
.btn {
    border: #00ffd2 1px solid;
    font-size: .675rem;
    padding: 6px 12px;
    border-radius: 4px;
    cursor: pointer;
    margin-top: 10px;
   }
}

</style>
