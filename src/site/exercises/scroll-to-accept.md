---
title: Scroll to accept (JS)
layout: layouts/blank.njk
date: 2020-12-19
meta: Scroll to accept terms and conditions exercise in JavaScript
tags: exercises
# img: https://jessbudd.com/images/featured/quoteGenerator.png
# excerpt: Need a quick pick-me-up? Cute puppers and floofers and doggos waiting for you in here.
---

<h1>{{title}}</h1>

  <div class="wrapper">
    <div class="terms-and-conditions">
      <p>Lorem, ipsum dolor sit amet consectetur adipisicing elit. Iste, labore!</p>
      <p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Rerum assumenda, ullam, sed quo ipsam officia
        asperiores minima excepturi eveniet reiciendis velit debitis temporibus explicabo. Incidunt sit itaque,
        reprehenderit fuga voluptatem officiis corrupti ipsa eveniet architecto dolorem magni facere doloribus aut
        veritatis sequi quia repellendus aperiam assumenda exercitationem optio praesentium debitis. Excepturi unde
        minus dignissimos at totam tempora beatae cumque, voluptates adipisci repudiandae asperiores repellat delectus
        tempore voluptatem veritatis atque quaerat optio! Quasi, possimus molestiae hic modi quia minus eius veniam
        aperiam assumenda fugiat fugit optio odio quas esse quam architecto officiis sunt quis cupiditate vel
        voluptate
        consequuntur nam porro harum. Fuga distinctio voluptate provident molestias perspiciatis fugit esse corrupti
        adipisci quas eos dolor non cum ipsam repudiandae dolorem, quasi necessitatibus iusto unde similique
        repellendus praesentium tenetur? Obcaecati aliquam nostrum vero expedita fuga, quae et quaerat modi error
        adipisci eligendi fugit alias quia nihil laudantium quam tenetur ipsam explicabo nisi natus, rerum omnis,
        debitis provident! Dolorum sequi recusandae, necessitatibus eos nesciunt cupiditate accusantium illum unde
        minima. Labore sit quos voluptatem illum qui. Veritatis quis a mollitia asperiores repudiandae consequatur
        assumenda, at tempora, modi voluptate sit blanditiis hic dignissimos harum consequuntur quia ipsam, architecto
        nesciunt. Praesentium, mollitia? Delectus quod laudantium doloremque nihil?</p>
      <p><strong class="watch">Watch for me</strong></p>
      <p>Lorem, ipsum dolor sit amet consectetur adipisicing elit. Quos ab, ea inventore commodi eligendi error
        repellat impedit eum quod enim sequi, distinctio, qui eaque ipsam fugit asperiores eos laboriosam ex.</p>
      <p>Lorem ipsum, dolor sit amet consectetur adipisicing elit. Ipsa id debitis ex eligendi rem unde consequuntur
        natus omnis vel nulla sit commodi, quos distinctio doloremque doloribus veniam quis et dolore?</p>
      <p>Lorem ipsum dolor sit amet consectetur, adipisicing elit. Commodi laboriosam nulla est architecto eum,
        dolorem
        quam, unde quo fugit tempore ipsa qui provident, iste ratione quis dignissimos temporibus nostrum voluptatum
        molestias? Blanditiis repellendus sapiente inventore aliquam qui error aliquid doloremque fugit consequuntur
        laudantium. Sapiente doloribus ullam vel dicta doloremque iure, deleniti ipsum non. Rem repudiandae deleniti
        ad
        at laborum eaque, modi voluptas aut! Quam nihil deleniti velit excepturi, quidem, veniam aut doloremque iure
        reprehenderit natus vel quia iusto? Magni veritatis provident libero hic quisquam, perferendis officia quasi
        molestiae sit sunt fugiat, perspiciatis architecto velit unde molestias ratione totam, atque doloremque!</p>
    </div>
    <!--
      autocomplete="off" adresses an issue with firefox
      where the browser will persist dynamic disabled state
      on buttons across page loads. More info here (se 'disabled' under 'Attributes')
      https://developer.mozilla.org/en-US/docs/Web/HTML/Element/button
This may or may not be desired in a real world scenario 🙃
    -->
    <button class="accept" disabled autocomplete="off">Accept</button>

  </div>

<script>

const terms = document.querySelector('.terms-and-conditions');
const watch = document.querySelecter('.watch');


function obCallback(payload) {
    console.log(payload);
}


const ob = new IntersectionObserver(obCallback);

// old way
// function scrollToAccept() {
//     if (!terms) {
//         return;
//     }
//         console.log(e.currentTarget.scrollTop);
//     })
// }


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
.wrapper {
      width: 400px;
      height: 75vh;
      padding: 20px;
      border: 1px solid black;
      background: white;
      display: grid;
      grid-template-rows: 1fr auto;
      margin-top: 20px;
    }
    h2 {
        color: purple;
        text-align: left;
    }
    p {
        color: #666;
        font-size: .875rem;
        text-align: left;
    }
    button {
      background: #ff0060;
      color: white;
      font-size: 1rem;
      padding: 20px;
      transition: all 0.2s;
    }
    button[disabled] {
      opacity: 0.1;
    }
    .terms-and-conditions {
      overflow: scroll;
    }
    footer {
        width: 100%;
    }

</style>
