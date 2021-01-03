---
title: Sarcastic Text Generator
# subtitle:
layout: layouts/blank.njk
date: 2019-12-12
meta: Convert your inputted text into another writing style.
excerpt:
# tags: funstuff, exercises
# img: https://jessbudd.com/images/featured/---.png
draft: true
---

<h1>{{ title }}</h1>

 <div class="typer">
    <label for="sarcastic">
      <input type="radio" value="sarcastic" id="sarcastic" name="filter" checked>
      Sarcastic
    </label>
    <label for="funky">
      <input type="radio" value="funky" id="funky" name="filter">
      Funky
    </label>
    <label for="unable">
      <input type="radio" value="unable" id="unable" name="filter">
      Unable to Structure a Sentence
    </label>
    <textarea name="text">so I was thinking about going to the store.</textarea>
    <p class="result"></p>
  </div>

<script>
const inputs = document.querySelectorAll('.typer input[type=radio]');
const text = document.querySelector('[name="text"');
const result = document.querySelector('.result');

// Set initial result to match text area
result.textContent = text.value;


function sarcastic() {
    console.log('sarcastic');
}
function funky() {
    console.log('funky');
}
function unable() {
    console.log('unable');
}
// inputs.forEach( input => addEventListener('input', handleInput));


function handleInput() {
    // set updated value of text
    result.textContent = text.value;
}
// check which radio button is selected
// match that name to function
// put text through function to style
// output text on page

// listen for keyup
text.addEventListener('keyup', handleInput);
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
    .typer {
      margin: 40px auto;
      background: white;
      width: 500px;
      padding: 2rem;
      padding: 2rem;
      border-radius: 3px;
      display: grid;
      text-align: left;
      color: #666;
    }
    p {
        color: #666;
    }
    textarea {
      width: 100%;
    }
    label,
    textarea {
        margin: 5px 0;
    }
  </style>
