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
const tabs = document.querySelector('.tabs');
const tabButtons = tabs.querySelectorAll('[role="tab"]');
const tabPanels = Array.from(tabs.querySelectorAll('[role="tabpanel"]'));

function handleTabClick(event) {
    // hide all tab panels
    tabPanels.forEach(panel => {
        panel.hidden = true;
    })
    // mark all tabs as unselected
    tabButtons.forEach(tab => {
        tab.setAttribute('aria-selected', false);
    });
    // mark the clicked tab as selected
    event.currentTarget.setAttribute('aria-selected', true);
    // find the associated tabpanel and show it
    const tabId = event.currentTarget.id;

    // Method 1 option
    // const tabPanel = tabs.querySelector(`[aria-labelledby="${tabId}"]`);
    // tabPanel.hidden = false;

    // Method 2 option (somewhat preferred)
    // find in the array of tabpanels (update tabPanel nodelist to array first)
    const tabPanel = tabPanels.find(panel => panel.getAttribute('aria-labelledby') === tabId);
    tabPanel.hidden = false;
    }

tabButtons.forEach(button => button.addEventListener('click', handleTabClick));

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
}
.tabs {
  display: grid;
  margin-top: 40px;
}

[role="tablist"] {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
  grid-gap: 10px;
}

[role="tabpanel"] {
  background: #1ac5c3;
  padding: 2rem;
}
button {
  background: #cec2ef;
  border: 0;
  color: black;
  border-radius: 5px 5px 0 0;
  --bs-color: rgba(0,0,0,0.1);
  box-shadow: inset 0 -2px 5px var(--bs-color);
  cursor:pointer;
  padding: 1em;
}

button[aria-selected="true"] {
  background: #1ac5c3;
  box-shadow: none;
  color: #fff;
}

button:focus {
  outline: 0;
  --bs-color: rgba(0,0,0,0.6);
}
footer {
    width: 100%;
}

</style>
