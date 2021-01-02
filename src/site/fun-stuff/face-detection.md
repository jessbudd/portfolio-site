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

<script>


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
      display: grid;
    align-items: center;
    justify-items: center;
}
</style>
