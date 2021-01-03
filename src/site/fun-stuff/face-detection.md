---
title: Face Detection & Pixelation
# subtitle:
layout: layouts/blank.njk
date: 2021-01-02
meta: Pixelising faces with the experimental Face Detector browser API
excerpt: Playing around with the experimental Face Detector Browser API. Finds/follows your face and pixelises it!
tags: funstuff
# img: https://jessbudd.com/images/featured/---.png
draft: true
---

<h1>{{ title }}</h1>

{%- if subtitle %}<p class='subtitle'>{{ subtitle | safe }}</p>{% endif %}

<div class="fail">
    <p>Hi there 👋</p>
    <p>I've been playing with Chrome's experimental Face Detector API, which is what this face detector pixelizor thingo uses.</p>
    <p> Unfortunately, it's only available behind a feature flag in Chrome on MacOS, Windows 10 and Android at the moment.</p> 
    <p>If you want to see what I've been playing around with, load up Chrome and visit <a href="chrome://flags/#enable-experimental-web-platform-features">chrome://flags/#enable-experimental-web-platform-features</a>.</p>
    <p> Then set the "experimental-web-platform-features" flag to enabled.
    </p>
    <p>(You'll also need to allow camera permissions when prompted.)</p>
</div>

<div class="controls">
    <label for="SIZE">
    Pixelation:
        <input name="SIZE" type="range" min="5" max="105" value="10" step="10">
    </label>
    <label for="SCALE">
    Scale:
        <input name="SCALE" type="range" min="0.3" max="3.3" value="1.4" step="1">
    </label>
</div>
<div class="fail2">
    <p>This page requires permission to use your camera.</p>
    <p>Don't worry - it won't record, store or transmit any video - this is just for fun!</p>
    <p>You can enable camera permissions (for this domain only) by clicking on the video icon in the right hand side of the address bar.</p> 
    <p>After accepting permssions, refresh the page and Bob's your uncle!</p> 
</div>
<div class="wrap">
    <video class="webcam" width="1080"></video>
    <canvas class="video"></canvas>
    <canvas class="face"></canvas>
  </div>

<script>
// The face detection does not work on all browsers and operating systems.
// If you are getting a `Face detection service unavailable` error or similar,
// it's possible that it won't work for you at the moment.

const failMessage = document.querySelector('.fail');
const wrap = document.querySelector('.wrap');
const video = document.querySelector('.webcam');
const canvas = document.querySelector('.video');
const ctx = canvas.getContext('2d');
const faceCanvas = document.querySelector('.face');
const faceCtx = faceCanvas.getContext('2d');
const optionControls = document.querySelectorAll('.controls input[type="range"');

const options = {
    SIZE: 15,
    SCALE: 1.4,
}

// check if faceDetector is supported
// if not supported, show fail message
if (!window.FaceDetector) {
    const controls = document.querySelector('.controls');
    failMessage.style.display = "block";
    wrap.style.display = "none";
    controls.style.display = "none";
    video.style.display = "none";
    console.log("FaceDetector API not available");
}

function errorMessage() {
    const failMessage2 = document.querySelector('.fail2');
    failMessage2.style.display = "block";
}

const faceDetector = new window.FaceDetector();

function handleInput(event) {
    // destructured because variable name is same as key
   const { value, name } = event.target;   
   options[name] = value; 
}
optionControls.forEach( input => input.addEventListener('input', handleInput))

// populate the users video
async function populateVideo() {
    const stream = await navigator.mediaDevices.getUserMedia({
        video: {
            width: 1080,
            height: 620,
        }
    });
    // success
    video.srcObject = stream;
    await video.play();
    // size the canvases to be same size as video
    canvas.width = video.videoWidth;
    canvas.height = video.videoHeight;
    faceCanvas.width = video.videoWidth;
    faceCanvas.height = video.videoHeight;
}

async function detect() {
    const faces = await faceDetector.detect(video);
    // console.log(faces);
    // ask browser when next animation frame is
    // and tell it to run detect for us
    faces.forEach(drawFace);
    faces.forEach(censor);
    requestAnimationFrame(detect);
}

function drawFace(face) {
    // destructured because variable name is same as object key
    const { width, height, left, top } = face.boundingBox;
    // clear the previous canvas image
    ctx.clearRect(0,0, canvas.width, canvas.height);
    ctx.strokeStyle = '#583ca0';
    ctx.lineWidth = 1;
    ctx.strokeRect(left, top, width, height);
    // wrapped in curly braces to log as object with key/value pair
    // works because property and variable name is same
    // console.log({ width, height, left, top })
}

// destructured takes boundingBox and renames it face
function censor({ boundingBox: face}) {
    faceCtx.imageSmoothEnabled = false;
    // clear the previous canvas image
    faceCtx.clearRect(0,0, faceCanvas.width, faceCanvas.height);
    // draw the small face
    faceCtx.drawImage(
        // 5 source args (draw data out)
        video, // where does source come from?
        face.x, // where to start source pull fomr?
        face.y,
        face.width,
        face.height,
        // 4 draw args (putting data back)
        face.x, // where should we start drawing?
        face.y,
        options.SIZE,
        options.SIZE,
    );
    // take small face, blow it up to normal size and draw back
    const width = face.width * options.SCALE;
    const height = face.height * options.SCALE;
    faceCtx.drawImage(
        faceCanvas, // source
        face.x, // where do we start the source pull?
        face.y,
        options.SIZE,
        options.SIZE,
        // drawing args
        face.x - (width - face.width) / 2,
        face.y - (height - face.height) / 2,
        width,
        height,
    );
    // console.log(face);
}

populateVideo().then(detect).catch(e => {
    errorMessage();
    console.error("Boo, Face Detection failed: " + e);
});



</script>

<style>
body {
    min-height: 100vh;
    display: grid;
    align-items: center;
    justify-items: center;
      margin: 0;
}

.container {
  text-align: center;
  margin: 2% auto 0;
      display: grid;
    align-items: center;
    justify-items: center;
}
.fail,
.fail2 {
    margin-top: 2% auto;
    display: none;
    text-align: left;
    max-width: 40em;
}
.fail2 {
    border: #00ffd2 1px solid;
    padding: 10px 20px;
    margin: 20px;
}
.fail2 p {
    color: #00ffd2;

}
* {
    box-sizing: border-box;
}
.wrap {
    position: relative;
    display: grid;
    justify-content: center;
    align-items: center;
}
.wrap>* {
    grid-column: 1;
    grid-row: 1;
}
.controls {
    margin: 40px 0 20px;
}
.face {
    position: absolute;
}
video,
canvas {
    max-width: 100%;
}
</style>
