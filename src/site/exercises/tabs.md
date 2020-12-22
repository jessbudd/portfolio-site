---
title: Tabs (JS & ARIA)
layout: layouts/blank.njk
date: 2020-12-22
meta: Accessible tabs exercise in JavaScript
tags: exercises
# img: https://jessbudd.com/images/featured/quoteGenerator.png
# excerpt: Need a quick pick-me-up? Cute puppers and floofers and doggos waiting for you in here.
---

<h1>{{title}}</h1>

<div class="wrapper">
    <div class="tabs">
      <div role="tablist" aria-label="Programming Languages">
        <button role="tab" aria-selected="true" id="js">
          JavaScript
        </button>
        <button role="tab" aria-selected="false" id="ruby">Ruby
        </button>
        <button role="tab" aria-selected="false" id="php">
          PHP
        </button>
      </div>
      <div role="tabpanel" aria-labelledby="js">
        <p>JavaScript is great!</p>
      </div>
      <div role="tabpanel" aria-labelledby="ruby" hidden>
        <p>Ruby is great</p>
      </div>
      <div role="tabpanel" aria-labelledby="php" hidden>
        <p>PHP is great!</p>
      </div>
    </div>
  </div>

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
.tabs {
  display: grid;
}

[role="tablist"] {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
  grid-gap: 10px;
}

[role="tabpanel"] {
  background: yellow;
  padding: 2rem;
}
button {
  background: grey;
  border: 0;
  color: black;
  border-radius: 5px 5px 0 0;
  --bs-color: rgba(0,0,0,0.1);
  box-shadow: inset 0 -2px 5px var(--bs-color);
  cursor:pointer;
}

button[aria-selected="true"] {
  background: yellow;
  box-shadow: none;
  color: rgba(0,0,0,0.7);
}

button:focus {
  outline: 0;
  --bs-color: rgba(0,0,0,0.6);
}
footer {
    width: 100%;
}

</style>
