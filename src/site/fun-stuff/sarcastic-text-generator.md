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
      <input type="radio" value="funky" id="funky" name="filter" >
      Funky
    </label>
    <label for="unable">
      <input type="radio" value="unable" id="unable" name="filter">
      Unable to Structure a Sentence
    </label>
    <textarea name="text" placeholder="Type your text here"></textarea>
    <p class="result"></p>
    <!-- <button id="copy">Copy Text</button> -->
  </div>

<script>

// function copy() {
//     console.log(result);
    
//   result.select();
//   document.execCommand("copy");
// }

// document.querySelector("#copy").addEventListener("click", copy);


const textarea = document.querySelector('[name="text"');
var result = document.querySelector('.result');
const inputs = Array.from(document.querySelectorAll('.typer input[name=filter]'));

/* eslint-disable */
const funkyLetters = {
  '-': '₋', '!': 'ᵎ', '?': 'ˀ', '(': '⁽', ')': '₎', '+': '⁺', '=': '₌', '0': '⁰', '1': '₁', '2': '²', '4': '₄', '5': '₅', '6': '₆', '7': '⁷', '8': '⁸', '9': '⁹', a: 'ᵃ', A: 'ᴬ', B: 'ᴮ', b: 'ᵦ', C: '𝒸', d: 'ᵈ', D: 'ᴰ', e: 'ₑ', E: 'ᴱ', f: '𝒻', F: 'ᶠ', g: 'ᵍ', G: 'ᴳ', h: 'ʰ', H: 'ₕ', I: 'ᵢ', i: 'ᵢ', j: 'ʲ', J: 'ᴶ', K: 'ₖ', k: 'ₖ', l: 'ˡ', L: 'ᴸ', m: 'ᵐ', M: 'ₘ', n: 'ₙ', N: 'ᴺ', o: 'ᵒ', O: 'ᴼ', p: 'ᵖ', P: 'ᴾ', Q: 'ᵠ', q: 'ᑫ', r: 'ʳ', R: 'ᵣ', S: 'ˢ', s: 'ˢ', t: 'ᵗ', T: 'ₜ', u: 'ᵘ', U: 'ᵤ', v: 'ᵛ', V: 'ᵥ', w: '𝓌', W: 'ʷ', x: 'ˣ', X: 'ˣ', y: 'y', Y: 'Y', z: '𝓏', Z: 'ᶻ'
};
/* eslint-enable */

// create object that holds our transform functions
const filters = {
    sarcastic: function(letter, index) {
        if(index % 2) {
            return letter.toUpperCase()
        }
        return letter.toLowerCase();        
    },
    funky: function(letter) {
        // check if funky letter exists
        let funkyLetter = funkyLetters[letter];
        if (funkyLetter) return funkyLetter;
        // if not, check if lowercase exists
        funkyLetter = funkyLetters[letter.toLowerCase()];
        if (funkyLetter) return funkyLetter;
        // if not, return regular letter
        return letter;
        console.log("funky");
    },
    unable: function(letter) {
        // every random third word
        const random =  Math.floor(Math.random() * 3);
        // add "...."
        if (letter === ' ' && random === 2) {
            return '...';
        }
        return letter;
        console.log("unable");
        
    },
}

function transformText(text) {
    const filter = inputs.find( input => input.checked).value;
    console.log(filter);
    
    // take the text, and loop over each letter
    const mod = Array.from(text).map(filters[filter]);
    result.textContent = mod.join('');
}


textarea.addEventListener('input', event => transformText(event.target.value));

inputs.forEach(input => 
    input.addEventListener('input', () => transformText(textarea.value)));

// TODO: Add copy to clipboard button

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
