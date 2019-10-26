---
title: Hiding Content Accessibly
subtitle: 
date: 2019-10-25
meta: 
# img: https://jessbudd.com/images/featured/confSpeaker.png
# tag: speaking
---

There are often situations in web development where we need to hide content, either temporarily or permanently. However different techniques for hiding content will have different impacts on people using assistive technologies, such as screen readers. 

This means particular techniques will be more appropriate for certain situations.

I want to quickly cover some of those situations, and which method would be appropriate to ensure web accessibility. 

<!-- If you're new to accessibility, I recommend checking out <a href="#">Microsoft's What Is Inclusive Design</a>. -->

There are generally 3 scenarios where we want to hide content:

- We want to hide content for everyone, including people using screen readers.
- We want to hide content visually, but not from screenreaders
- We want to hide content from screenreaders, but not visually

## Hiding content for everyone

Usecase:

Method:
<pre>
<code class="language-css">
display: none;
</code>
</pre>

<pre>
<code class="language-css">
visibility: hidden;
</code>
</pre>

<pre>
<code class="language-css">
width:0px, 
height:0px
</code>
</pre>

These styles will hide text from all users. The text is removed from the visual flow of the page and is ignored by screen readers. Do not use this CSS if you want the content to be read by a screen reader. But DO use it for content you don't want read by screen readers.

## Hiding content visually

### Never visible

There are times when the visual information in a design is not sufficient for screen readers users. A common example of this is form inputs that aren't given visual labels. 

Labels are imperitive for screen reader users to understand and successfully complete forms. So in a situation like this you could visually hide the programatically linked label with CSS. 

There are a few different methods to achieve this, however the most commonly accepted practice for modern browser support is using clip-rect. The CSS would be as below.


<pre>
<code class="language-css">
.sr-only {
    clip: rect(1px, 1px, 1px, 1px);
    clip-path: inset(50%);
    height: 1px;
    width: 1px;
    margin: -1px;
    overflow: hidden;
    padding: 0;
    position: absolute;
}
</code>
</pre>

Elements with this class would be invisible to a sighted person and does not take up any space in the visual flow. If this element is focusable (for example a link), it would remain invisbile when focused. 

### Visble when focused

Sometimes we want to hide an element only until it recieves keyboard focus. 

A perfect example of this is [skip-links](https://webaim.org/techniques/skipnav/). A skip-link is styled with CSS to remain out of view until a user tabs to the element with a keyboard and then sent back out of view when it leaves focus. This behaviour benefits sighted keyboard users, for example people with mobility impairments.


<pre>
<code class="language-css">
.skip-link a {
    position: absolute;
    left: -10000px;
    top: auto;
    width: 1px;
    height: 1px;
    overflow: hidden;
}

.skip-link a:focus {
    position: static;
    width: auto;
    height: auto;
}

</code>
</pre>



## Hiding content from screen readers

Usecase:

Sometimes we have a situation where we need to remove a visual item from the accessiblity tree. Examples of this would be an


this can also be achieved with 

<pre>
<code class="language-markup">
&lt;div aria-hidden="true">I am hidden from the accessibility tree&lt;/div>
</code>
</pre>

## Further Reading

If you're interested in learning more about hiding content accessibly I've included some links to more information below:

- [Invisible Content Just For Screen Readers by WebAIM](https://webaim.org/techniques/css/invisiblecontent/)
- [How to Hide Content by The A11y Project](https://a11yproject.com/posts/how-to-hide-content/)
- [Inclusively Hidden by Scott O'Hara](https://www.scottohara.me/blog/2017/04/14/inclusively-hidden.html)

