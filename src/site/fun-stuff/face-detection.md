---
title: Face Detection
# subtitle:
layout: layouts/blank.njk
date: 2021-01-02
meta:
excerpt:
# tags: funstuff
# img: https://jessbudd.com/images/featured/---.png
draft: true
---

<h1>{{ title }}</h1>

{%- if subtitle %}<p class='subtitle'>{{ subtitle | safe }}</p>{% endif %}

<!-- This page requires the experimental Face Detection API to work. To enable Chrome face detection go to `chrome://flags/#enable-experimental-web-platform-features`
And click enable.-->
<div class="controls">
    <label for="SIZE">
    Size:
        <input name="SIZE" type="range" min="1" max="100" value="10" step="1">
    </label>
    <label for="SCALE">
    Scale:
        <input name="SCALE" type="range" min="0.3" max="3" value="1.4" step="0.1">
    </label>
</div>
<div class="wrap">
    <video class="webcam"></video>
    <canvas class="video"></canvas>
    <canvas class="face"></canvas>
  </div>

<script>
// The face detection does not work on all browsers and operating systems.
// If you are getting a `Face detection service unavailable` error or similar,
// it's possible that it won't work for you at the moment.

const video = document.querySelector('.webcam');
const canvas = document.querySelector('.video');
const ctx = canvas.getContext('2d');
const faceCanvas = document.querySelector('.face');
const faceCtx = faceCanvas.getContext('2d');

const faceDetector = new window.FaceDetector();
const optionControls = document.querySelectorAll('.controls input[type="range"');
console.log(optionControls);


const options = {
    SIZE: 10,
    SCALE: 1.4,
}
function handleInput(event) {
   console.log(event.target);
    
}
optionControls.forEach( input => input.addEventListener('input', handleInput))

// populate the users video
async function populateVideo() {
    const stream = await navigator.mediaDevices.getUserMedia({
        video: {
            width: 980,
            height: 620,
        }
    });
    // console.log(stream);
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

populateVideo().then(detect);



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
.face {
    position: absolute;
}
</style>
