---
title: Inspirational Women Quote Generator
layout: layouts/blank.njk
date: 2019-12-05
meta: A simple generator of inspirational quotes from women
tags: funstuff
img: https://jessbudd.com/images/featured/quoteGenerator.png
excerpt: A friend was recently given a list of inspirational quotes to add to a student handbook. Out of the 40+ quotes (one for each school week), only two were from women. So I decided to showcase more than 60 quotes from women.
---

 <link href="https://fonts.googleapis.com/css?family=Julius+Sans+One|Nanum+Myeongjo&display=swap" rel="stylesheet"> 
<div class="quote-generator">
<!-- <h1>{{title}}</h1> -->

<div class="quote__wrapper">
    <blockquote id="quote" class="quote">The most dangerous phrase in the language is, "We've always done it this way."</blockquote>
    <cite id="author" class="author">Grace Hopper</cite>
</div>

<button class="btn" onclick="getNewQuote()">Get new quote</button>

<div class="share-links">
<a id="tweetQuote" class="btn btn__twitter" target="_blank"  href="">Tweet this quote</a>
<a id ="shareTool" class="btn btn__twitter" target="_blank" href="https://twitter.com/intent/tweet?text=In%20need%20some%20inspiration?%20Check%20out%20this%20Quote%20Generator%20by%20@jessbudd4%20bit.ly/klsjdhfk">Share generator</a>
</div>

<section class="why">

<h2 class="h4">Why make this?</h2>

A friend was recently given a list of inspirational quotes to add to a student handbook. Out of the 40+ quotes (one for each school week), only two were from women. So I decided to showcase more than 60 quotes from women. Also, for funsies 🙂

<!-- <h2 class="h4">Can I see the whole list of quotes?</h2>

Sure, why not.

<button>Generate full list of quotes</button> -->

</section>

</div>

<style>

/* fun stuff styles */
.quote-generator {
  text-align: center;
  padding-top: 100px;
  max-width: 900px;
  margin: 0 auto;
}
.quote__wrapper {
    min-height: 300px;
    padding-top: 72px;
}

blockquote {
    font-size: 2.6rem;
    border-left-width: 5px; 
    padding: 12px 30px;
    line-height: 1.5;
    font-family: 'Nanum Myeongjo', serif;
}
cite {
    font-family: 'Nanum Myeongjo', serif;
}

@media (max-width: 900px) {
    blockquote {
    font-size: 2rem;
    line-height: 1.5;
    }
    cite {
        font-family: 'Nanum Myeongjo', serif;
    }
}

@media (max-width: 600px) {
.quote-generator {
  padding-top: 50px;
}
.quote__wrapper {
    min-height: 300px;
    padding-top: 42px;
            transition: opacity 2s ease-in;
}
  blockquote {
    font-size: 1.6rem;
    }
}

.share-links {
    padding: 50px 0;
}
.why {
    text-align: left;
}
.why p {
    font-size: .975rem;
}
button {
    display: block;
    margin: 0 auto;
}
footer {
    padding-top: 2em;
    padding-bottom: 2em;
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
}

.share-links {
    margin-top: 24px;
}
a.btn__twitter {
  font-family: "Helvetica Neue", Verdana, Helvetica, Arial, sans-serif;
display: block;
background-color: #55acee;
transition: opacity 0.2s ease-in, top 0.2s ease-in;
border-radius: 4px;
border: none;
cursor: pointer;
display: inline-block;
font-size: .875rem;
height: 32px;
line-height: 32px;
margin-right: 8px;
margin-left: 8px;
padding: 0px 18px;
font-weight: bold;
}  
a.btn__twitter:before {
    content: url("/images/icons/twitter-white.svg");
    margin-right: 18px;
    position: relative;
    top: 3px;
}
@media (max-width: 600px) {
a.btn__twitter {
    width: 80%;
    margin-top: 12px;
}
}
</style>

<script>
var quote = document.getElementById('quote');
var author = document.getElementById('author');
// var url = document.getElementById('url');

// update share tool link href
var shareToolText = 'In need of some inspiration? Try this inspirational women quote generator by @jessbudd4 bit.ly/klsjdhfk ';
var shareTool = shareToolText.split(' ').join('%20');
shareTool = "https://twitter.com/intent/tweet?text=" + shareTool.split('"').join('') ;
document.getElementById('shareTool').setAttribute('href', shareTool);

// set tweet quote link href
var credit = '' 
var tweetQuoteText = document.getElementById('tweetQuote');
var tweetQuote = quote.innerHTML.split(' ').join('%20') + '%22%20-%20' + author.innerHTML.split(' ').join('%20');
tweetQuote = "https://twitter.com/intent/tweet?text=\"" + tweetQuote.split('"').join('') + credit;;
tweetQuoteText.setAttribute('href', tweetQuote);


function getNewQuote() {
    if (quotes.length > 0 ) {
        var randomNumber = Math.floor(Math.random()*(quotes.length));
        quote.innerText = quotes[randomNumber].quote;
        author.innerText = quotes[randomNumber].author;

        //remove quote from array
        quotes.splice(randomNumber,1);

        // update tweet quote link href
        tweetQuote = '';
        tweetQuote = quote.innerHTML.split(' ').join('%20')+ '%22%20-%20' + author.innerHTML.split(' ').join('%20');
        tweetQuote = "https://twitter.com/intent/tweet?text=\"" + tweetQuote.split('"').join('') + credit;
        tweetQuoteText.setAttribute('href', tweetQuote);
    } 
    else {
        quote.innerText = 'That\'s all folks!';
        author.innerText = '';
    }
}

// array of quotes
var quotes = [
{
quote: 'You don\'t manage people, you manage things. You lead people.',
author: 'Grace Hopper',
url: 'https://www.biography.com/scientist/grace-hopper'
},
{
quote: 'It is often easier to ask for forgiveness than to ask for permission.',
author: 'Grace Hopper',
url: 'https://www.biography.com/scientist/grace-hopper'
},
//{
// quote: 'The most dangerous phrase in the language is, \"We\'ve always done it this way.\"',
// author: 'Grace Hopper',
// url: 'https://www.biography.com/scientist/grace-hopper'
// },
{
quote: 'A ship in port is safe, but that is not what ships are for.',
author: 'Grace Hopper',
url: 'whttps://www.biography.com/scientist/grace-hopper'
},
{
quote: 'One accurate measurement is worth a thousand expert opinions.',
author: 'Grace Hopper',
url: 'https://www.biography.com/scientist/grace-hopper'
},
{
quote: 'All great achievements require time.',
author: 'Maya Angelou',
url: ''
},
{
quote: 'If you don\'t like something, change it. If you can\'t change it, change your attitude.',
author: 'Maya Angelou',
url: ''
},
{
quote: 'Nothing will work unless you do.',
author: 'Maya Angelou',
url: ''
},
{
quote: 'Life is what you make it. Always has been, always will be.',
author: 'Eleanor Roosevelt',
url: ''
},
{
quote: 'You don\’t have to be someone special to achieve something amazing. You\’ve just got to have a dream, believe in it and work hard.',
author: 'Jessica Watson',
url: ''
},
{
quote: 'Don\'t feel stupid if you don\'t like what everyone else pretends to love.',
author: 'Emma Watson',
url: ''
},
{
quote: 'When the whole world is silent, even one voice becomes powerful.',
author: 'Malala Yousafzai',
url: ''
},
{
quote: 'The most difficult thing is the decision to act, the rest is merely tenacity.',
author: 'Amelia Earhart',
url: ''
},
{
quote: 'In order to be irreplaceable one must always be different.',
author: 'Coco Chanel',
url: ''
},
{
quote: 'Being confident and believing in your own self-worth is necessary to achieving your potential.',
author: 'Sheryl Sandberg',
url: ''
},
{
quote: 'Done is better than perfect.',
author: 'Sheryl Sandberg',
url: ''
},
// {
// quote: 'Don\'t let anyone rob you of your imagination, your creativity, or your curiosity. It\'s your place in the world; it\'s your life. Go on and do all you can with it, and make it the life you want to live.',
// author: 'Mae Jemison',
// url: 'https://www.space.com/17169-mae-jemison-biography.html'
// },
{
quote: 'I was taught that the way of progress was neither swift nor easy.',
author: 'Marie Curie',
url: 'https://www.brainyquote.com/quotes/marie_curie_383419'
},
{
quote: 'Life need not be easy, provided only that it is not empty.',
author: 'Lise Meitner',
url: 'https://www.goodreads.com/quotes/1336078-life-need-not-be-easy-provided-only-that-it-is'
},
{
quote: 'All sorts of things can happen when you\’re open to new ideas and playing around with things.',
author: 'Stephanie Kwolek',
url: 'http://www2.dupont.com/Kevlar/en_US/assets/downloads/DuPont_Cooper_River_Timeline_Online_Piece_FINAL%20100311.pdf'
},
{
quote: 'As always in life, people want a simple answer...and it\’s always wrong.',
author: 'Susan Greenfield',
url: 'http://extraordinarywls.blogspot.com/2016/01/quote-susan-greenfield.html'
},
{
quote: 'Courage is like a habitus, a habit, a virtue: you get it by courageous acts. It\’s like you learn to swim by swimming. You learn courage by couraging',
author: 'Marie Daly',
url: 'https://www.biography.com/people/marie-m-daly-604034'
},
{
quote: 'The more clearly we can focus our attention on the wonders and realities of the universe about us, the less taste we shall have for destruction.',
author: 'Rachel Carson',
url: 'https://www.americanswhotellthetruth.org/portraits/rachel-carson'
},
{
quote: 'Make the most of yourself by fanning the tiny, inner sparks of possibility into flames of achievement.',
author: 'Golda Meir',
url: 'http://www.goodreads.com/author/quotes/223411.Golda_Meir'
},
{
quote: 'I didn\’t get there by wishing for it or hoping for it, but by working for it.',
author: 'Estée Lauder',
url: ''
},
{
quote: 'Power\’s not given to you. You have to take it.',
author: 'Beyoncé Knowles Carter',
url: ''
},
{
quote: 'The difference between successful people and others is how long they spend time feeling sorry for themselves.',
author: 'Barbara Corcoran',
url: ''
},
{
quote: 'You can waste your lives drawing lines. Or you can live your life crossing them.',
author: 'Shonda Rhimes',
url: ''
},
{
quote: 'I\’d rather regret the things I\’ve done than regret the things I haven\’t done.',
author: 'Lucille Ball',
url: ''
},
{
quote: 'If you don\’t risk anything, you risk even more.',
author: 'Erica Jong',
url: ''
},
{
quote: 'A woman is like a tea bag - you can\'t tell how strong she is until you put her in hot water.',
author: 'Eleanor Roosevelt',
url: ''
},
{
quote: 'If you don\’t like the road you\’re walking, start paving another one.',
author: 'Dolly Parton',
url: ''
},
{
quote: 'One of the secrets to staying young is to always do things you don\’t know how to do, to keep learning.',
author: 'Ruth Reichl',
url: ''
},
{
quote: 'It took me quite a long time to develop a voice, and now that I have it, I am not going to be silent.',
author: 'Madeleine Albright',
url: ''
},
{
quote: 'Step out of the history that is holding you back. Step into the new story you are willing to create.',
author: 'Oprah Winfrey',
url: ''
},
{
quote: 'What you do makes a difference, and you have to decide what kind of difference you want to make.',
author: 'Jane Goodall',
url: ''
},
{
quote: 'I choose to make the rest of my life the best of my life.',
author: 'Louise Hay',
url: ''
},
{
quote: 'The question isn\’t who is going to let me; it\’s who is going to stop me.',
author: 'Ayn Rand',
url: ''
},
{
quote: 'Take criticism seriously, but not personally. If there is truth or merit in the criticism, try to learn from it. Otherwise, let it roll right off you.',
author: 'Hillary Clinton',
url: ''
},
{
quote: 'When we speak we are afraid our words will not be heard or welcomed. But when we are silent, we are still afraid. So it is better to speak.',
author: 'Audre Lorde',
url: ''
},
{
quote: 'Learn from the mistakes of others. You can\’t live long enough to make them all yourself.',
author: 'Eleanor Roosevelt',
url: ''
},
{
quote: 'If you\’re not making some notable mistakes along the way, you\’re certainly not taking enough business and career chances.',
author: 'Sallie Krawcheck',
url: ''
},
{
quote: 'Doubt is a killer. You just have to know who you are and what you stand for.',
author: 'Jennifer Lopez',
url: ''
},
{
quote: 'I am not afraid of storms for I am learning how to sail my ship.',
author: 'Louisa May Alcott',
url: ''
},
{
quote: 'When you feel copied, remember that people can only go where you have already been, they have no idea where you are going next.”',
author: 'Liz Lange',
url: ''
},
{
quote: 'Hold your head and your standards high even as people or circumstances try to pull you down.',
author: 'Tory Johnson',
url: ''
},
{
quote: 'Normal is not something to aspire to, it\’s something to get away from.',
author: 'Jodie Foster',
url: ''
},
{
quote: 'I learned a long time ago that there is something worse than missing the goal, and that\’s not pulling the trigger.',
author: 'Mia Hamm',
url: ''
},
{
quote: 'Owning our story can be hard but not nearly as difficult as spending our lives running from it.',
author: 'Brene Brown',
url: ''
},
{
quote: 'I do not try to dance better than anyone else. I only try to dance better than myself.',
author: 'Arianna Huffington',
url: ''
},
{
quote: 'I\’m always perpetually out of my comfort zone.',
author: 'Tory Burch',
url: ''
},
{
quote: 'If you can\’t go straight ahead, you go around the corner.',
author: 'Cher',
url: ''
},
{
quote: 'If you don\’t get out of the box you’ve been raised in, you won\’t understand how much bigger the world is.”',
author: 'Angelina Jolie',
url: ''
},
{
quote: 'Everyone shines, given the right lighting.',
author: 'Susan Cain',
url: ''
},
{
quote: 'When you embrace your difference, your DNA, your look or heritage or religion or your unusual name, that’s when you start to shine.',
author: 'Bethenny Frankel',
url: ''
},
{
quote: 'You can\’t be that kid standing at the top of the waterslide, overthinking it. You have to go down the chute.',
author: 'Tina Fey  ',
url: ''
},
{
quote: 'If you just set out to be liked, you would be prepared to compromise on anything at any time, and you would achieve nothing.',
author: 'Margaret Thatcher',
url: ''
},
{
quote: 'Don\’t look at your feet to see if you are doing it right. Just dance.',
author: 'Anne Lamott',
url: ''
},
{
quote: 'All careers go up and down like friendships, like marriages, like anything else, and you can’t bat a thousand all the time.',
author: 'Julie Andrews',
url: ''
},
{
quote: 'We do not need magic to change the world, we carry all the power we need inside ourselves already: we have the power to imagine better.',
author: 'J.K. Rowling',
url: ''
},
{
quote: 'Dying seems less sad than having lived too little.',
author: 'Gloria Steinem',
url: ''
},
{
quote: 'Style is a way to say who you are without having to speak.',
author: 'Rachel Zoe',
url: ''
},
{
quote: 'I need to listen well so that I hear what is not said.',
author: 'Thuli Madonsela',
url: ''
},
{
quote: 'Style is a way to say who you are without having to speak.',
author: 'Rachel Zoe',
url: ''
},
{
quote: 'It’s not the absence of fear, it’s overcoming it. Sometimes you’ve got to blast through and have faith.',
author: 'Emma Watson',
url: ''
}
]

</script>
