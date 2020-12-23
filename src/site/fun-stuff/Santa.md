---
title: Help Santa
layout: layouts/blank.njk
date: 2020-12-22
meta: Animation, JavaScript practice
tags: funstuff
# img: https://jessbudd.com/images/featured/quoteGenerator.png
excerpt: It's Christmas Eve and Santa needs help getting to his sleigh! Can you get him where he needs to be?
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
<img src="/images/funstuff/santa.png" alt="cartoon santa" id="santa" width="120" style="">

<p>Help Santa get back to his sleigh using the arrow keys or buttons.</p>
</div>

<ul class="g-snows" id="jsi-snows">
  <li></li>
  <li></li>
  <li></li>
  <li></li>
  <li></li>
  <li></li>
  <li></li>
  <li></li>
  <li></li>
  <li></li>
  <li></li>
  <li></li>
  <li></li>
  <li></li>
  <li></li>
  <li></li>
  <li></li>
  <li></li>
  <li></li>
  <li></li>
  <li></li>
  <li></li>
  <li></li>
  <li></li>
  <li></li>
  <li></li>
  <li></li>
  <li></li>
  <li></li>
  <li></li>
  <li></li>
  <li></li>
  <li></li>
  <li></li>
  <li></li>
  <li></li>
  <li></li>
  <li></li>
  <li></li>
  <li></li>
  <li></li>
  <li></li>
  <li></li>
  <li></li>
  <li></li>
  <li></li>
  <li></li>
  <li></li>
  <li></li>
  <li></li>
  <li></li>
  <li></li>
  <li></li>
  <li></li>
  <li></li>
  <li></li>
  <li></li>
  <li></li>
  <li></li>
  <li></li>
  <li></li>
  <li></li>
  <li></li>
  <li></li>
  <li></li>
  <li></li>
  <li></li>
  <li></li>
  <li></li>
  <li></li>
  <li></li>
  <li></li>
  <li></li>
  <li></li>
  <li></li>
  <li></li>
  <li></li>
  <li></li>
  <li></li>
  <li></li>
  <li></li>
  <li></li>
  <li></li>
  <li></li>
  <li></li>
  <li></li>
  <li></li>
  <li></li>
  <li></li>
  <li></li>
  <li></li>
  <li></li>
  <li></li>
  <li></li>
  <li></li>
  <li></li>
  <li></li>
  <li></li>
  <li></li>
  <li></li>
</ul>

<script>

const controls = document.querySelectorAll('.control');
const santa = document.querySelector('#santa');
const wrapper = document.querySelector('.wrapper');

const speed = 10;
const MOVE_AMOUNT = 3;

const imgHeight = 120;
let height = window.innerHeight;
let width = window.innerWidth;
let randomHeight = randomPosition((height / 2), height);
let randomWidth = randomPosition((width / 2), width);
let x = 0;
let y = 0;
let flipped = false;
let rotate = 0;

    function randomPosition(min, max) {
    min = Math.ceil(min);
    max = Math.floor(max - 200);
    return Math.floor(Math.random() * (max - min) + min);
}

window.addEventListener('resize', function() {
height = window.innerHeight;
width = window.innerWidth;
})

function addSleighOnLoad() {
    const sleigh = document.createElement('img');
    sleigh.src = "/images/funstuff/sleigh.png";
    sleigh.alt = "cartoon sleigh";
    sleigh.width =`${imgHeight}`;
    sleigh.id = "sleigh";
    sleigh.style.position = 'absolute';

    sleigh.style.top = `${randomHeight}px`;
    sleigh.style.left = `${randomWidth}px`;

    wrapper.appendChild(sleigh);

}

function resetGame() {
const sleigh = document.querySelector('#sleigh');
const newRandomHeight = randomPosition((height / 2), height);
const newRandomWidth = randomPosition((width / 2), width);
randomHeight = newRandomHeight;
randomWidth = newRandomWidth;
sleigh.style.top = `${newRandomHeight}px`;
sleigh.style.left = `${newRandomWidth}px`;

    santa.setAttribute(`style`, `
        --y: 0px;
        --x: 0px;
    `);
    x = 0;
    y = 0;

}

function moveTurtle(command) {

    const isOutOfViewport = function(element) {
        // Get element's bounding
        const bounding = element.getBoundingClientRect();
        // Check if it's out of the viewport on each side
        let out = {};
        out.top = (bounding.top) < 0;
        out.left = (bounding.left) < 0;
        out.bottom = (bounding.bottom) > height;
        out.right = (bounding.right - 10) > width;
        return out;
    };

    const isOut = isOutOfViewport(santa);
    let foundSleigh = false;

    if(command === "ArrowUp" && !isOut.top) {
         y = y - MOVE_AMOUNT;
    } else if (command === "ArrowRight" && !isOut.right) {
        x = x + MOVE_AMOUNT;
        flipped = false;
    } else if (command === "ArrowDown" && !isOut.bottom) {
        y = y + MOVE_AMOUNT;
    } else if (command === "ArrowLeft" && !isOut.left) {
         x = x - MOVE_AMOUNT;
        flipped = true;
    } else {
        return;
    }

    const isRotatedLeft = santa.getAttribute('style').includes('-6deg');
    if (isRotatedLeft) {
         santa.setAttribute(`style`, `
            --y: ${y * speed}px;
            --x: ${x * speed}px;
            --rotate: 6deg;
        `);
    } else {
        santa.setAttribute(`style`, `
            --y: ${y * speed}px;
            --x: ${x * speed}px;
            --rotate: -6deg;
        `);
    }

    // make arrow button light up when corresponding arrow key is used
    const arrow = document.querySelector(`#${command}`);
    arrow.focus()

    const santaLocationX = parseInt(santa.getBoundingClientRect().x);
    const santaLocationY = parseInt(santa.getBoundingClientRect().y);
    const sleighLocationX = parseInt(sleigh.getBoundingClientRect().x);
    const sleighLocationY = parseInt(sleigh.getBoundingClientRect().y);
    const isMobile = width < 450;

    const isTurtleOnX = santaLocationX > (sleighLocationX - (isMobile ? 50 : 75)) && santaLocationX < (sleighLocationX +

(isMobile ? 50 : 75));

    const isTurtleOnY = santaLocationY > (sleighLocationY - (isMobile ? 50 : 50)) && santaLocationY < (sleighLocationY + (isMobile ? 50 : 50));

    // console.log(`santalocationX ${santaLocationX}
    // santalocationY ${santaLocationY}
    // ${isTurtleOnX} ${isTurtleOnY}
    // sleigh X ${sleighLocationX} slieigh Y$ {sleighLocationY}`);

    if(isTurtleOnX && isTurtleOnY) {
        foundSleigh = true;
    }

    if (foundSleigh) {
        foundSleigh = false;
        alert(`Thanks friend! You helped Santa to his sleigh just in time to deliver all the presents!`);
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

addSleighOnLoad();

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
#santa {
    position: relative;
    --x: 0;
    --y: 0;
    --rotate: 0;
    transform: translateX(var(--x)) translateY(var(--y)) rotate(var(--rotate));
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

#sleigh {
    width: 80px;
}
#santa {
    width: 80px;
}
.btn {
    font-size: .675rem;
    padding: 6px 12px;
   }
}

/* Snow effect by https://codepen.io/kyoyababa/pen/OWJaoB */


.g-snows {
  width: 100vw;
  height: 100vh;
  position: absolute;
  top: 0;
  left: 0;
  pointer-events: none;
}

.g-snows > li {
  opacity: 0;
  position: absolute;
  top: 0;
  border-radius: 100%;
  background-color: #FFFFFF;
  background-repeat: no-repeat;
  background-size: 100% auto;
  -webkit-animation-name: snow-drop;
          animation-name: snow-drop;
  -webkit-animation-iteration-count: infinite;
          animation-iteration-count: infinite;
  -webkit-animation-timing-function: linear;
          animation-timing-function: linear;
  -webkit-animation-fill-mode: forwards;
          animation-fill-mode: forwards;
}
.g-snows > li:nth-child(1) {
  left: 89%;
  width: 3px;
  height: 3px;
  -webkit-animation-duration: 5931ms;
          animation-duration: 5931ms;
  -webkit-animation-delay: 2475ms;
          animation-delay: 2475ms;
  -webkit-filter: blur(0px);
          filter: blur(0px);
}
.g-snows > li:nth-child(2) {
  left: 11%;
  width: 4px;
  height: 4px;
  -webkit-animation-duration: 7611ms;
          animation-duration: 7611ms;
  -webkit-animation-delay: 4660ms;
          animation-delay: 4660ms;
  -webkit-filter: blur(1px);
          filter: blur(1px);
}
.g-snows > li:nth-child(3) {
  left: 20%;
  width: 22px;
  height: 22px;
  -webkit-animation-duration: 7307ms;
          animation-duration: 7307ms;
  -webkit-animation-delay: 1787ms;
          animation-delay: 1787ms;
  -webkit-filter: blur(1px);
          filter: blur(1px);
}
.g-snows > li:nth-child(4) {
  left: 38%;
  width: 11px;
  height: 11px;
  -webkit-animation-duration: 5347ms;
          animation-duration: 5347ms;
  -webkit-animation-delay: 3722ms;
          animation-delay: 3722ms;
  -webkit-filter: blur(1px);
          filter: blur(1px);
}
.g-snows > li:nth-child(5) {
  left: 40%;
  width: 22px;
  height: 22px;
  -webkit-animation-duration: 8956ms;
          animation-duration: 8956ms;
  -webkit-animation-delay: 61ms;
          animation-delay: 61ms;
  -webkit-filter: blur(0px);
          filter: blur(0px);
}
.g-snows > li:nth-child(6) {
  left: 34%;
  width: 24px;
  height: 24px;
  -webkit-animation-duration: 5230ms;
          animation-duration: 5230ms;
  -webkit-animation-delay: 1353ms;
          animation-delay: 1353ms;
  -webkit-filter: blur(2px);
          filter: blur(2px);
}
.g-snows > li:nth-child(7) {
  left: 56%;
  width: 24px;
  height: 24px;
  -webkit-animation-duration: 7609ms;
          animation-duration: 7609ms;
  -webkit-animation-delay: 3834ms;
          animation-delay: 3834ms;
  -webkit-filter: blur(2px);
          filter: blur(2px);
}
.g-snows > li:nth-child(8) {
  left: 6%;
  width: 8px;
  height: 8px;
  -webkit-animation-duration: 10568ms;
          animation-duration: 10568ms;
  -webkit-animation-delay: 3619ms;
          animation-delay: 3619ms;
  -webkit-filter: blur(3px);
          filter: blur(3px);
}
.g-snows > li:nth-child(9) {
  left: 28%;
  width: 2px;
  height: 2px;
  -webkit-animation-duration: 6327ms;
          animation-duration: 6327ms;
  -webkit-animation-delay: 2957ms;
          animation-delay: 2957ms;
  -webkit-filter: blur(3px);
          filter: blur(3px);
}
.g-snows > li:nth-child(10) {
  left: 1%;
  width: 7px;
  height: 7px;
  -webkit-animation-duration: 6485ms;
          animation-duration: 6485ms;
  -webkit-animation-delay: 2867ms;
          animation-delay: 2867ms;
  -webkit-filter: blur(3px);
          filter: blur(3px);
}
.g-snows > li:nth-child(11) {
  left: 2%;
  width: 5px;
  height: 5px;
  -webkit-animation-duration: 6551ms;
          animation-duration: 6551ms;
  -webkit-animation-delay: 3810ms;
          animation-delay: 3810ms;
  -webkit-filter: blur(0px);
          filter: blur(0px);
}
.g-snows > li:nth-child(12) {
  left: 85%;
  width: 16px;
  height: 16px;
  -webkit-animation-duration: 7590ms;
          animation-duration: 7590ms;
  -webkit-animation-delay: 2975ms;
          animation-delay: 2975ms;
  -webkit-filter: blur(0px);
          filter: blur(0px);
}
.g-snows > li:nth-child(13) {
  left: 86%;
  width: 25px;
  height: 25px;
  -webkit-animation-duration: 6525ms;
          animation-duration: 6525ms;
  -webkit-animation-delay: 1212ms;
          animation-delay: 1212ms;
  -webkit-filter: blur(2px);
          filter: blur(2px);
}
.g-snows > li:nth-child(14) {
  left: 69%;
  width: 4px;
  height: 4px;
  -webkit-animation-duration: 12113ms;
          animation-duration: 12113ms;
  -webkit-animation-delay: 1348ms;
          animation-delay: 1348ms;
  -webkit-filter: blur(0px);
          filter: blur(0px);
}
.g-snows > li:nth-child(15) {
  left: 30%;
  width: 3px;
  height: 3px;
  -webkit-animation-duration: 13991ms;
          animation-duration: 13991ms;
  -webkit-animation-delay: 2513ms;
          animation-delay: 2513ms;
  -webkit-filter: blur(0px);
          filter: blur(0px);
}
.g-snows > li:nth-child(16) {
  left: 50%;
  width: 25px;
  height: 25px;
  -webkit-animation-duration: 7857ms;
          animation-duration: 7857ms;
  -webkit-animation-delay: 2812ms;
          animation-delay: 2812ms;
  -webkit-filter: blur(2px);
          filter: blur(2px);
}
.g-snows > li:nth-child(17) {
  left: 25%;
  width: 13px;
  height: 13px;
  -webkit-animation-duration: 8550ms;
          animation-duration: 8550ms;
  -webkit-animation-delay: 3134ms;
          animation-delay: 3134ms;
  -webkit-filter: blur(1px);
          filter: blur(1px);
}
.g-snows > li:nth-child(18) {
  left: 38%;
  width: 10px;
  height: 10px;
  -webkit-animation-duration: 7116ms;
          animation-duration: 7116ms;
  -webkit-animation-delay: 1853ms;
          animation-delay: 1853ms;
  -webkit-filter: blur(2px);
          filter: blur(2px);
}
.g-snows > li:nth-child(19) {
  left: 123%;
  width: 20px;
  height: 20px;
  -webkit-animation-duration: 9826ms;
          animation-duration: 9826ms;
  -webkit-animation-delay: 3968ms;
          animation-delay: 3968ms;
  -webkit-filter: blur(1px);
          filter: blur(1px);
}
.g-snows > li:nth-child(20) {
  left: 94%;
  width: 18px;
  height: 18px;
  -webkit-animation-duration: 9249ms;
          animation-duration: 9249ms;
  -webkit-animation-delay: 4693ms;
          animation-delay: 4693ms;
  -webkit-filter: blur(1px);
          filter: blur(1px);
}
.g-snows > li:nth-child(21) {
  left: 114%;
  width: 13px;
  height: 13px;
  -webkit-animation-duration: 5528ms;
          animation-duration: 5528ms;
  -webkit-animation-delay: 3397ms;
          animation-delay: 3397ms;
  -webkit-filter: blur(2px);
          filter: blur(2px);
}
.g-snows > li:nth-child(22) {
  left: 7%;
  width: 1px;
  height: 1px;
  -webkit-animation-duration: 12765ms;
          animation-duration: 12765ms;
  -webkit-animation-delay: 2547ms;
          animation-delay: 2547ms;
  -webkit-filter: blur(0px);
          filter: blur(0px);
}
.g-snows > li:nth-child(23) {
  left: 39%;
  width: 10px;
  height: 10px;
  -webkit-animation-duration: 9059ms;
          animation-duration: 9059ms;
  -webkit-animation-delay: 2216ms;
          animation-delay: 2216ms;
  -webkit-filter: blur(1px);
          filter: blur(1px);
}
.g-snows > li:nth-child(24) {
  left: 7%;
  width: 26px;
  height: 26px;
  -webkit-animation-duration: 5978ms;
          animation-duration: 5978ms;
  -webkit-animation-delay: 3642ms;
          animation-delay: 3642ms;
  -webkit-filter: blur(0px);
          filter: blur(0px);
}
.g-snows > li:nth-child(25) {
  left: 43%;
  width: 4px;
  height: 4px;
  -webkit-animation-duration: 6487ms;
          animation-duration: 6487ms;
  -webkit-animation-delay: 523ms;
          animation-delay: 523ms;
  -webkit-filter: blur(1px);
          filter: blur(1px);
}
.g-snows > li:nth-child(26) {
  left: 5%;
  width: 2px;
  height: 2px;
  -webkit-animation-duration: 5306ms;
          animation-duration: 5306ms;
  -webkit-animation-delay: 874ms;
          animation-delay: 874ms;
  -webkit-filter: blur(0px);
          filter: blur(0px);
}
.g-snows > li:nth-child(27) {
  left: 33%;
  width: 13px;
  height: 13px;
  -webkit-animation-duration: 5943ms;
          animation-duration: 5943ms;
  -webkit-animation-delay: 4345ms;
          animation-delay: 4345ms;
  -webkit-filter: blur(0px);
          filter: blur(0px);
}
.g-snows > li:nth-child(28) {
  left: 93%;
  width: 1px;
  height: 1px;
  -webkit-animation-duration: 6573ms;
          animation-duration: 6573ms;
  -webkit-animation-delay: 703ms;
          animation-delay: 703ms;
  -webkit-filter: blur(0px);
          filter: blur(0px);
}
.g-snows > li:nth-child(29) {
  left: 81%;
  width: 2px;
  height: 2px;
  -webkit-animation-duration: 5773ms;
          animation-duration: 5773ms;
  -webkit-animation-delay: 467ms;
          animation-delay: 467ms;
  -webkit-filter: blur(2px);
          filter: blur(2px);
}
.g-snows > li:nth-child(30) {
  left: 43%;
  width: 9px;
  height: 9px;
  -webkit-animation-duration: 6940ms;
          animation-duration: 6940ms;
  -webkit-animation-delay: 2644ms;
          animation-delay: 2644ms;
  -webkit-filter: blur(1px);
          filter: blur(1px);
}
.g-snows > li:nth-child(31) {
  left: 103%;
  width: 17px;
  height: 17px;
  -webkit-animation-duration: 14034ms;
          animation-duration: 14034ms;
  -webkit-animation-delay: 3273ms;
          animation-delay: 3273ms;
  -webkit-filter: blur(2px);
          filter: blur(2px);
}
.g-snows > li:nth-child(32) {
  left: 42%;
  width: 7px;
  height: 7px;
  -webkit-animation-duration: 5160ms;
          animation-duration: 5160ms;
  -webkit-animation-delay: 2434ms;
          animation-delay: 2434ms;
  -webkit-filter: blur(0px);
          filter: blur(0px);
}
.g-snows > li:nth-child(33) {
  left: 43%;
  width: 11px;
  height: 11px;
  -webkit-animation-duration: 11273ms;
          animation-duration: 11273ms;
  -webkit-animation-delay: 332ms;
          animation-delay: 332ms;
  -webkit-filter: blur(1px);
          filter: blur(1px);
}
.g-snows > li:nth-child(34) {
  left: 64%;
  width: 20px;
  height: 20px;
  -webkit-animation-duration: 8787ms;
          animation-duration: 8787ms;
  -webkit-animation-delay: 36ms;
          animation-delay: 36ms;
  -webkit-filter: blur(4px);
          filter: blur(4px);
}
.g-snows > li:nth-child(35) {
  left: 101%;
  width: 10px;
  height: 10px;
  -webkit-animation-duration: 5341ms;
          animation-duration: 5341ms;
  -webkit-animation-delay: 1259ms;
          animation-delay: 1259ms;
  -webkit-filter: blur(3px);
          filter: blur(3px);
}
.g-snows > li:nth-child(36) {
  left: 49%;
  width: 14px;
  height: 14px;
  -webkit-animation-duration: 13306ms;
          animation-duration: 13306ms;
  -webkit-animation-delay: 2343ms;
          animation-delay: 2343ms;
  -webkit-filter: blur(1px);
          filter: blur(1px);
}
.g-snows > li:nth-child(37) {
  left: 8%;
  width: 3px;
  height: 3px;
  -webkit-animation-duration: 10581ms;
          animation-duration: 10581ms;
  -webkit-animation-delay: 2834ms;
          animation-delay: 2834ms;
  -webkit-filter: blur(2px);
          filter: blur(2px);
}
.g-snows > li:nth-child(38) {
  left: 1%;
  width: 13px;
  height: 13px;
  -webkit-animation-duration: 5455ms;
          animation-duration: 5455ms;
  -webkit-animation-delay: 1173ms;
          animation-delay: 1173ms;
  -webkit-filter: blur(0px);
          filter: blur(0px);
}
.g-snows > li:nth-child(39) {
  left: 124%;
  width: 11px;
  height: 11px;
  -webkit-animation-duration: 12842ms;
          animation-duration: 12842ms;
  -webkit-animation-delay: 1284ms;
          animation-delay: 1284ms;
  -webkit-filter: blur(1px);
          filter: blur(1px);
}
.g-snows > li:nth-child(40) {
  left: 55%;
  width: 13px;
  height: 13px;
  -webkit-animation-duration: 6451ms;
          animation-duration: 6451ms;
  -webkit-animation-delay: 1682ms;
          animation-delay: 1682ms;
  -webkit-filter: blur(0px);
          filter: blur(0px);
}
.g-snows > li:nth-child(41) {
  left: 20%;
  width: 21px;
  height: 21px;
  -webkit-animation-duration: 9163ms;
          animation-duration: 9163ms;
  -webkit-animation-delay: 2974ms;
          animation-delay: 2974ms;
  -webkit-filter: blur(2px);
          filter: blur(2px);
}
.g-snows > li:nth-child(42) {
  left: 2%;
  width: 1px;
  height: 1px;
  -webkit-animation-duration: 10109ms;
          animation-duration: 10109ms;
  -webkit-animation-delay: 432ms;
          animation-delay: 432ms;
  -webkit-filter: blur(1px);
          filter: blur(1px);
}
.g-snows > li:nth-child(43) {
  left: 11%;
  width: 9px;
  height: 9px;
  -webkit-animation-duration: 9897ms;
          animation-duration: 9897ms;
  -webkit-animation-delay: 865ms;
          animation-delay: 865ms;
  -webkit-filter: blur(1px);
          filter: blur(1px);
}
.g-snows > li:nth-child(44) {
  left: 35%;
  width: 24px;
  height: 24px;
  -webkit-animation-duration: 7073ms;
          animation-duration: 7073ms;
  -webkit-animation-delay: 4585ms;
          animation-delay: 4585ms;
  -webkit-filter: blur(3px);
          filter: blur(3px);
}
.g-snows > li:nth-child(45) {
  left: 3%;
  width: 3px;
  height: 3px;
  -webkit-animation-duration: 5299ms;
          animation-duration: 5299ms;
  -webkit-animation-delay: 2067ms;
          animation-delay: 2067ms;
  -webkit-filter: blur(1px);
          filter: blur(1px);
}
.g-snows > li:nth-child(46) {
  left: 71%;
  width: 16px;
  height: 16px;
  -webkit-animation-duration: 9113ms;
          animation-duration: 9113ms;
  -webkit-animation-delay: 3920ms;
          animation-delay: 3920ms;
  -webkit-filter: blur(0px);
          filter: blur(0px);
}
.g-snows > li:nth-child(47) {
  left: 115%;
  width: 16px;
  height: 16px;
  -webkit-animation-duration: 5947ms;
          animation-duration: 5947ms;
  -webkit-animation-delay: 1531ms;
          animation-delay: 1531ms;
  -webkit-filter: blur(1px);
          filter: blur(1px);
}
.g-snows > li:nth-child(48) {
  left: 76%;
  width: 11px;
  height: 11px;
  -webkit-animation-duration: 10305ms;
          animation-duration: 10305ms;
  -webkit-animation-delay: 502ms;
          animation-delay: 502ms;
  -webkit-filter: blur(2px);
          filter: blur(2px);
}
.g-snows > li:nth-child(49) {
  left: 23%;
  width: 18px;
  height: 18px;
  -webkit-animation-duration: 13570ms;
          animation-duration: 13570ms;
  -webkit-animation-delay: 931ms;
          animation-delay: 931ms;
  -webkit-filter: blur(1px);
          filter: blur(1px);
}
.g-snows > li:nth-child(50) {
  left: 37%;
  width: 2px;
  height: 2px;
  -webkit-animation-duration: 7085ms;
          animation-duration: 7085ms;
  -webkit-animation-delay: 1703ms;
          animation-delay: 1703ms;
  -webkit-filter: blur(0px);
          filter: blur(0px);
}
.g-snows > li:nth-child(51) {
  left: 34%;
  width: 7px;
  height: 7px;
  -webkit-animation-duration: 11520ms;
          animation-duration: 11520ms;
  -webkit-animation-delay: 2492ms;
          animation-delay: 2492ms;
  -webkit-filter: blur(0px);
          filter: blur(0px);
}
.g-snows > li:nth-child(52) {
  left: 26%;
  width: 8px;
  height: 8px;
  -webkit-animation-duration: 14396ms;
          animation-duration: 14396ms;
  -webkit-animation-delay: 1124ms;
          animation-delay: 1124ms;
  -webkit-filter: blur(1px);
          filter: blur(1px);
}
.g-snows > li:nth-child(53) {
  left: 32%;
  width: 20px;
  height: 20px;
  -webkit-animation-duration: 9400ms;
          animation-duration: 9400ms;
  -webkit-animation-delay: 3320ms;
          animation-delay: 3320ms;
  -webkit-filter: blur(1px);
          filter: blur(1px);
}
.g-snows > li:nth-child(54) {
  left: 85%;
  width: 0px;
  height: 0px;
  -webkit-animation-duration: 5090ms;
          animation-duration: 5090ms;
  -webkit-animation-delay: 3568ms;
          animation-delay: 3568ms;
  -webkit-filter: blur(3px);
          filter: blur(3px);
}
.g-snows > li:nth-child(55) {
  left: 90%;
  width: 4px;
  height: 4px;
  -webkit-animation-duration: 6192ms;
          animation-duration: 6192ms;
  -webkit-animation-delay: 2029ms;
          animation-delay: 2029ms;
  -webkit-filter: blur(4px);
          filter: blur(4px);
}
.g-snows > li:nth-child(56) {
  left: 22%;
  width: 8px;
  height: 8px;
  -webkit-animation-duration: 7079ms;
          animation-duration: 7079ms;
  -webkit-animation-delay: 3084ms;
          animation-delay: 3084ms;
  -webkit-filter: blur(0px);
          filter: blur(0px);
}
.g-snows > li:nth-child(57) {
  left: 81%;
  width: 7px;
  height: 7px;
  -webkit-animation-duration: 9734ms;
          animation-duration: 9734ms;
  -webkit-animation-delay: 2942ms;
          animation-delay: 2942ms;
  -webkit-filter: blur(1px);
          filter: blur(1px);
}
.g-snows > li:nth-child(58) {
  left: 16%;
  width: 20px;
  height: 20px;
  -webkit-animation-duration: 7763ms;
          animation-duration: 7763ms;
  -webkit-animation-delay: 4387ms;
          animation-delay: 4387ms;
  -webkit-filter: blur(1px);
          filter: blur(1px);
}
.g-snows > li:nth-child(59) {
  left: 77%;
  width: 10px;
  height: 10px;
  -webkit-animation-duration: 5804ms;
          animation-duration: 5804ms;
  -webkit-animation-delay: 2364ms;
          animation-delay: 2364ms;
  -webkit-filter: blur(0px);
          filter: blur(0px);
}
.g-snows > li:nth-child(60) {
  left: 36%;
  width: 13px;
  height: 13px;
  -webkit-animation-duration: 5907ms;
          animation-duration: 5907ms;
  -webkit-animation-delay: 766ms;
          animation-delay: 766ms;
  -webkit-filter: blur(0px);
          filter: blur(0px);
}
.g-snows > li:nth-child(61) {
  left: 58%;
  width: 4px;
  height: 4px;
  -webkit-animation-duration: 7675ms;
          animation-duration: 7675ms;
  -webkit-animation-delay: 4685ms;
          animation-delay: 4685ms;
  -webkit-filter: blur(1px);
          filter: blur(1px);
}
.g-snows > li:nth-child(62) {
  left: 19%;
  width: 11px;
  height: 11px;
  -webkit-animation-duration: 8212ms;
          animation-duration: 8212ms;
  -webkit-animation-delay: 1038ms;
          animation-delay: 1038ms;
  -webkit-filter: blur(0px);
          filter: blur(0px);
}
.g-snows > li:nth-child(63) {
  left: 104%;
  width: 13px;
  height: 13px;
  -webkit-animation-duration: 7644ms;
          animation-duration: 7644ms;
  -webkit-animation-delay: 4418ms;
          animation-delay: 4418ms;
  -webkit-filter: blur(4px);
          filter: blur(4px);
}
.g-snows > li:nth-child(64) {
  left: 113%;
  width: 5px;
  height: 5px;
  -webkit-animation-duration: 10941ms;
          animation-duration: 10941ms;
  -webkit-animation-delay: 1321ms;
          animation-delay: 1321ms;
  -webkit-filter: blur(1px);
          filter: blur(1px);
}
.g-snows > li:nth-child(65) {
  left: 34%;
  width: 14px;
  height: 14px;
  -webkit-animation-duration: 7164ms;
          animation-duration: 7164ms;
  -webkit-animation-delay: 79ms;
          animation-delay: 79ms;
  -webkit-filter: blur(0px);
          filter: blur(0px);
}
.g-snows > li:nth-child(66) {
  left: 6%;
  width: 22px;
  height: 22px;
  -webkit-animation-duration: 10427ms;
          animation-duration: 10427ms;
  -webkit-animation-delay: 4245ms;
          animation-delay: 4245ms;
  -webkit-filter: blur(2px);
          filter: blur(2px);
}
.g-snows > li:nth-child(67) {
  left: 68%;
  width: 16px;
  height: 16px;
  -webkit-animation-duration: 5923ms;
          animation-duration: 5923ms;
  -webkit-animation-delay: 597ms;
          animation-delay: 597ms;
  -webkit-filter: blur(1px);
          filter: blur(1px);
}
.g-snows > li:nth-child(68) {
  left: 6%;
  width: 0px;
  height: 0px;
  -webkit-animation-duration: 5973ms;
          animation-duration: 5973ms;
  -webkit-animation-delay: 2365ms;
          animation-delay: 2365ms;
  -webkit-filter: blur(0px);
          filter: blur(0px);
}
.g-snows > li:nth-child(69) {
  left: 43%;
  width: 4px;
  height: 4px;
  -webkit-animation-duration: 11705ms;
          animation-duration: 11705ms;
  -webkit-animation-delay: 2724ms;
          animation-delay: 2724ms;
  -webkit-filter: blur(2px);
          filter: blur(2px);
}
.g-snows > li:nth-child(70) {
  left: 24%;
  width: 3px;
  height: 3px;
  -webkit-animation-duration: 12646ms;
          animation-duration: 12646ms;
  -webkit-animation-delay: 2329ms;
          animation-delay: 2329ms;
  -webkit-filter: blur(3px);
          filter: blur(3px);
}
.g-snows > li:nth-child(71) {
  left: 79%;
  width: 22px;
  height: 22px;
  -webkit-animation-duration: 8180ms;
          animation-duration: 8180ms;
  -webkit-animation-delay: 13ms;
          animation-delay: 13ms;
  -webkit-filter: blur(0px);
          filter: blur(0px);
}
.g-snows > li:nth-child(72) {
  left: 13%;
  width: 29px;
  height: 29px;
  -webkit-animation-duration: 6215ms;
          animation-duration: 6215ms;
  -webkit-animation-delay: 3160ms;
          animation-delay: 3160ms;
  -webkit-filter: blur(0px);
          filter: blur(0px);
}
.g-snows > li:nth-child(73) {
  left: 7%;
  width: 3px;
  height: 3px;
  -webkit-animation-duration: 9660ms;
          animation-duration: 9660ms;
  -webkit-animation-delay: 4987ms;
          animation-delay: 4987ms;
  -webkit-filter: blur(4px);
          filter: blur(4px);
}
.g-snows > li:nth-child(74) {
  left: 34%;
  width: 5px;
  height: 5px;
  -webkit-animation-duration: 12264ms;
          animation-duration: 12264ms;
  -webkit-animation-delay: 4055ms;
          animation-delay: 4055ms;
  -webkit-filter: blur(0px);
          filter: blur(0px);
}
.g-snows > li:nth-child(75) {
  left: 125%;
  width: 9px;
  height: 9px;
  -webkit-animation-duration: 8414ms;
          animation-duration: 8414ms;
  -webkit-animation-delay: 579ms;
          animation-delay: 579ms;
  -webkit-filter: blur(1px);
          filter: blur(1px);
}
.g-snows > li:nth-child(76) {
  left: 46%;
  width: 4px;
  height: 4px;
  -webkit-animation-duration: 9649ms;
          animation-duration: 9649ms;
  -webkit-animation-delay: 2351ms;
          animation-delay: 2351ms;
  -webkit-filter: blur(4px);
          filter: blur(4px);
}
.g-snows > li:nth-child(77) {
  left: 6%;
  width: 8px;
  height: 8px;
  -webkit-animation-duration: 6542ms;
          animation-duration: 6542ms;
  -webkit-animation-delay: 4449ms;
          animation-delay: 4449ms;
  -webkit-filter: blur(2px);
          filter: blur(2px);
}
.g-snows > li:nth-child(78) {
  left: 71%;
  width: 2px;
  height: 2px;
  -webkit-animation-duration: 9714ms;
          animation-duration: 9714ms;
  -webkit-animation-delay: 1613ms;
          animation-delay: 1613ms;
  -webkit-filter: blur(2px);
          filter: blur(2px);
}
.g-snows > li:nth-child(79) {
  left: 4%;
  width: 12px;
  height: 12px;
  -webkit-animation-duration: 6685ms;
          animation-duration: 6685ms;
  -webkit-animation-delay: 4306ms;
          animation-delay: 4306ms;
  -webkit-filter: blur(0px);
          filter: blur(0px);
}
.g-snows > li:nth-child(80) {
  left: 3%;
  width: 4px;
  height: 4px;
  -webkit-animation-duration: 9072ms;
          animation-duration: 9072ms;
  -webkit-animation-delay: 4522ms;
          animation-delay: 4522ms;
  -webkit-filter: blur(2px);
          filter: blur(2px);
}
.g-snows > li:nth-child(81) {
  left: 24%;
  width: 11px;
  height: 11px;
  -webkit-animation-duration: 13680ms;
          animation-duration: 13680ms;
  -webkit-animation-delay: 4573ms;
          animation-delay: 4573ms;
  -webkit-filter: blur(3px);
          filter: blur(3px);
}
.g-snows > li:nth-child(82) {
  left: 26%;
  width: 15px;
  height: 15px;
  -webkit-animation-duration: 11965ms;
          animation-duration: 11965ms;
  -webkit-animation-delay: 3041ms;
          animation-delay: 3041ms;
  -webkit-filter: blur(3px);
          filter: blur(3px);
}
.g-snows > li:nth-child(83) {
  left: 27%;
  width: 11px;
  height: 11px;
  -webkit-animation-duration: 5889ms;
          animation-duration: 5889ms;
  -webkit-animation-delay: 1865ms;
          animation-delay: 1865ms;
  -webkit-filter: blur(1px);
          filter: blur(1px);
}
.g-snows > li:nth-child(84) {
  left: 49%;
  width: 15px;
  height: 15px;
  -webkit-animation-duration: 7640ms;
          animation-duration: 7640ms;
  -webkit-animation-delay: 4852ms;
          animation-delay: 4852ms;
  -webkit-filter: blur(1px);
          filter: blur(1px);
}
.g-snows > li:nth-child(85) {
  left: 34%;
  width: 16px;
  height: 16px;
  -webkit-animation-duration: 6589ms;
          animation-duration: 6589ms;
  -webkit-animation-delay: 4707ms;
          animation-delay: 4707ms;
  -webkit-filter: blur(4px);
          filter: blur(4px);
}
.g-snows > li:nth-child(86) {
  left: 23%;
  width: 9px;
  height: 9px;
  -webkit-animation-duration: 6579ms;
          animation-duration: 6579ms;
  -webkit-animation-delay: 3400ms;
          animation-delay: 3400ms;
  -webkit-filter: blur(2px);
          filter: blur(2px);
}
.g-snows > li:nth-child(87) {
  left: 51%;
  width: 12px;
  height: 12px;
  -webkit-animation-duration: 10794ms;
          animation-duration: 10794ms;
  -webkit-animation-delay: 961ms;
          animation-delay: 961ms;
  -webkit-filter: blur(2px);
          filter: blur(2px);
}
.g-snows > li:nth-child(88) {
  left: 83%;
  width: 24px;
  height: 24px;
  -webkit-animation-duration: 12435ms;
          animation-duration: 12435ms;
  -webkit-animation-delay: 691ms;
          animation-delay: 691ms;
  -webkit-filter: blur(1px);
          filter: blur(1px);
}
.g-snows > li:nth-child(89) {
  left: 32%;
  width: 12px;
  height: 12px;
  -webkit-animation-duration: 8350ms;
          animation-duration: 8350ms;
  -webkit-animation-delay: 4718ms;
          animation-delay: 4718ms;
  -webkit-filter: blur(1px);
          filter: blur(1px);
}
.g-snows > li:nth-child(90) {
  left: 6%;
  width: 10px;
  height: 10px;
  -webkit-animation-duration: 6307ms;
          animation-duration: 6307ms;
  -webkit-animation-delay: 2742ms;
          animation-delay: 2742ms;
  -webkit-filter: blur(2px);
          filter: blur(2px);
}
.g-snows > li:nth-child(91) {
  left: 18%;
  width: 6px;
  height: 6px;
  -webkit-animation-duration: 7548ms;
          animation-duration: 7548ms;
  -webkit-animation-delay: 3036ms;
          animation-delay: 3036ms;
  -webkit-filter: blur(0px);
          filter: blur(0px);
}
.g-snows > li:nth-child(92) {
  left: 28%;
  width: 7px;
  height: 7px;
  -webkit-animation-duration: 6360ms;
          animation-duration: 6360ms;
  -webkit-animation-delay: 4339ms;
          animation-delay: 4339ms;
  -webkit-filter: blur(0px);
          filter: blur(0px);
}
.g-snows > li:nth-child(93) {
  left: 92%;
  width: 8px;
  height: 8px;
  -webkit-animation-duration: 5769ms;
          animation-duration: 5769ms;
  -webkit-animation-delay: 4912ms;
          animation-delay: 4912ms;
  -webkit-filter: blur(1px);
          filter: blur(1px);
}
.g-snows > li:nth-child(94) {
  left: 32%;
  width: 4px;
  height: 4px;
  -webkit-animation-duration: 7186ms;
          animation-duration: 7186ms;
  -webkit-animation-delay: 4108ms;
          animation-delay: 4108ms;
  -webkit-filter: blur(1px);
          filter: blur(1px);
}
.g-snows > li:nth-child(95) {
  left: 41%;
  width: 7px;
  height: 7px;
  -webkit-animation-duration: 9050ms;
          animation-duration: 9050ms;
  -webkit-animation-delay: 1190ms;
          animation-delay: 1190ms;
  -webkit-filter: blur(1px);
          filter: blur(1px);
}
.g-snows > li:nth-child(96) {
  left: 134%;
  width: 11px;
  height: 11px;
  -webkit-animation-duration: 6751ms;
          animation-duration: 6751ms;
  -webkit-animation-delay: 4433ms;
          animation-delay: 4433ms;
  -webkit-filter: blur(1px);
          filter: blur(1px);
}
.g-snows > li:nth-child(97) {
  left: 49%;
  width: 20px;
  height: 20px;
  -webkit-animation-duration: 7135ms;
          animation-duration: 7135ms;
  -webkit-animation-delay: 1208ms;
          animation-delay: 1208ms;
  -webkit-filter: blur(1px);
          filter: blur(1px);
}
.g-snows > li:nth-child(98) {
  left: 12%;
  width: 14px;
  height: 14px;
  -webkit-animation-duration: 5060ms;
          animation-duration: 5060ms;
  -webkit-animation-delay: 732ms;
          animation-delay: 732ms;
  -webkit-filter: blur(2px);
          filter: blur(2px);
}
.g-snows > li:nth-child(99) {
  left: 49%;
  width: 20px;
  height: 20px;
  -webkit-animation-duration: 9065ms;
          animation-duration: 9065ms;
  -webkit-animation-delay: 1264ms;
          animation-delay: 1264ms;
  -webkit-filter: blur(3px);
          filter: blur(3px);
}
.g-snows > li:nth-child(100) {
  left: 59%;
  width: 21px;
  height: 21px;
  -webkit-animation-duration: 5762ms;
          animation-duration: 5762ms;
  -webkit-animation-delay: 712ms;
          animation-delay: 712ms;
  -webkit-filter: blur(0px);
          filter: blur(0px);
}

@-webkit-keyframes snow-drop {
  0% {
    -webkit-transform: translate(0, 0);
            transform: translate(0, 0);
    opacity: 0.5;
    margin-left: 0;
  }
  10% {
    margin-left: 15px;
  }
  20% {
    margin-left: 20px;
  }
  25% {
    -webkit-transform: translate(0, 166.6666666667px);
            transform: translate(0, 166.6666666667px);
    opacity: 0.75;
  }
  30% {
    margin-left: 15px;
  }
  40% {
    margin-left: 0;
  }
  50% {
    -webkit-transform: translate(0, 333.3333333333px);
            transform: translate(0, 333.3333333333px);
    opacity: 1;
    margin-left: -15px;
  }
  60% {
    margin-left: -20px;
  }
  70% {
    margin-left: -15px;
  }
  75% {
    -webkit-transform: translate(0, 500px);
            transform: translate(0, 500px);
    opacity: 0.5;
  }
  80% {
    margin-left: 0;
  }
  100% {
    -webkit-transform: translate(0, 666.6666666667px);
            transform: translate(0, 666.6666666667px);
    opacity: 0;
  }
}

@keyframes snow-drop {
  0% {
    -webkit-transform: translate(0, 0);
            transform: translate(0, 0);
    opacity: 0.5;
    margin-left: 0;
  }
  10% {
    margin-left: 15px;
  }
  20% {
    margin-left: 20px;
  }
  25% {
    -webkit-transform: translate(0, 166.6666666667px);
            transform: translate(0, 166.6666666667px);
    opacity: 0.75;
  }
  30% {
    margin-left: 15px;
  }
  40% {
    margin-left: 0;
  }
  50% {
    -webkit-transform: translate(0, 333.3333333333px);
            transform: translate(0, 333.3333333333px);
    opacity: 1;
    margin-left: -15px;
  }
  60% {
    margin-left: -20px;
  }
  70% {
    margin-left: -15px;
  }
  75% {
    -webkit-transform: translate(0, 500px);
            transform: translate(0, 500px);
    opacity: 0.5;
  }
  80% {
    margin-left: 0;
  }
  100% {
    -webkit-transform: translate(0, 666.6666666667px);
            transform: translate(0, 666.6666666667px);
    opacity: 0;
  }
}

</style>
