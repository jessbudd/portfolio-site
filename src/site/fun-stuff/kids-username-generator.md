---
title: Kids Username Generator
layout: layouts/blank.njk
date: 2020-01-01
meta:
tags: funstuff
# img: https://jessbudd.com/images/featured/quoteGenerator.png
excerpt: It's important for kids online safety to ensure usernames avoid any personal identifying giveaways. I made this little tool to help my kids pick out fun, easy to remember usernames.
---

<h1>{{title}}</h1>

<!-- TODO pick two words or three words option -->
<!-- TODO animate name coming in and going out -->

<section class="generator">

<div class="generatedName"><span style="opacity: 0;" aria-hidden="true">HoldingSpace</span></div>

<button class="btn" onClick="getFunName()">Generate username</button>

</section>

<section class="why">

<h2 class="h4">Why make this?</h2>

My kids and I have been talking about online safety lately and how important it is not to put out personally identifiable information into the webosphere. Part of those discussions are about [choosing safe screen names](https://www.moms.com/how-kids-choose-username-tips/), and how its also a good idea to [use unique usernames across different gaming platforms.](https://leapfrogservices.com/why-usernames-are-important-and-how-to-choose-good-ones/)

I thought this cute tool to help choose fun, non-identifiable usernames.

</section>

<style>
body {
    min-height: 100vh;
    display: grid;
}
.container {
  margin: 5% auto 0;
    text-align: center;

}
.generator {
    padding: 60px 0 80px;
}
.generatedName {
    font-size: 3rem;
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

.why {
    text-align: left;
}

</style>

<script>
const generatedNameContainer = document.querySelector('.generatedName');

function rando(arr) {
  return arr[Math.floor(Math.random() * arr.length)];
}

function toTitleCase(str) {
  return str.replace(
    /\w\S*/g,
    function(txt) {
      return txt.charAt(0).toUpperCase() + txt.substr(1).toLowerCase();
    }
  );
}

function toCamelCase(str) {
  return str.replace(/(?:^\w|[A-Z]|\b\w)/g, function(word, index) {
    return index === 0 ? word.toLowerCase() : word.toUpperCase();
  }).replace(/\s+/g, '');
}


function getFunName() {
  const adjectives = [
    "adorable",
    "funky",
    "elegant",
    "fancy",
    "glamorous",
    "handsome",
    "blueberry",
    "magnificent",
    "banana",
    "cherry",
    "quaint",
    "sparkling",
    "scrumptious",
    "minecraft",
    "purple",
    "pink",
    "blue",
    "yellow",
    "violet",
    "happy",
    "helpful",
    "sweet",
    "black",
    "white",
    "jumbo",
    "warm",
    "cold",
    "navy",
    "tooth",
    "awesome",
    "wicked",
    "cool",
    "delightful",
    "bubbly"

  ];

    const verbs = [
    "erupting",
    "biting",
    "blazing",
    "smiling",
    "camping",
    "travelling",
    "bathing",
    "sleeping",
    "stargazing",
    "jogging",
    "canoing",
    "drinking",
    "climbing",
    "driving",
    "swimming"
    ];

  const nouns = [
    "lolly",
    "cucumber",
    "carrot",
    "candy",
    "seal",
    "santa",
    "jeans",
    "lobster",
    "jellybeans",
    "cupcake",
    "apple",
    "pineapple",
    "miner",
    "wolf",
    "zombie",
    "enderdragon",
    "enderman",
    "lego",
    "puppy",
    "sky",
    "snow",
    "rain",
    "mountain",
    "stream",
    "pyjamas",
    "piglet",
    "tiger",
    "Aladdin",
    "Rapunzel",
    "blob",
    "ocolet",
    "trifle",
    "shopkin",
    "elf",
    "healer",
    "banquet",
    "bluey",
    "dingo",
    "elephant",
    "giraffe",
    "swan",
    "cheeta",
    "lion",
    "tree",
    "octopus",
    "grape",
    "shoe",
    "sock",
    "meadow",
    "firefighter",
    "pilot",
    "jungle",
    "bear",
    "river",
    "fairy", 
    "fairytale",
    "reindeer",
    "puzzle",
    "pancake",
    "bacon",
    "popsicle",
    "storm",
    "cloud",
    "poppy",
    "flower",
    "rose",
    "garden",
    "bubble",
    "bee",
    "bug",
    "gamer",
    "pikachu",
    "balbasaur",
    "snorlax",
    "charmander",
    "squirtle",
    "pokemon"
  ];

  const generatedName = (`${rando(adjectives)} ${rando(verbs)} ${rando(nouns)}`);

  generatedNameContainer.textContent = toCamelCase(generatedName);
}

</script>
