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

This page requires the experimental Face Detection API to work. To enable Chrome face detection go to
`chrome://flags/#enable-experimental-web-platform-features`
And click enable.

<div class="wrap">
    <video class="webcam"></video>
    <canvas class="video"></canvas>
    <canvas class="face"></canvas>
  </div>

<script>


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
    min-height: 100vh;
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
