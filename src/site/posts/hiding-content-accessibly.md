---
title: Hiding Content Accessibly
subtitle: 
date: 2019-10-29
meta: There are often situations where we need to hide content on a page, here's how to do so accessibily.
# img: https://jessbudd.com/images/featured/confSpeaker.png
# tag: speaking
---

<p class="subtitle">There are often situations where we need to hide content on a page, either temporarily or permanently. Different techniques will have differing impacts on accessibility, and certain methods are more appropriate for certain situations.</p> 

<!-- 
I want to quickly cover some of those situations, and which method would be appropriate to ensure web accessibility.  -->

<!-- If you're new to accessibility, I recommend checking out <a href="#">Microsoft's What Is Inclusive Design</a>. -->

There are generally 3 scenarios where we want to hide content:

1. We want to hide content for everyone (including people using screen readers).
1. We want to hide content visually (but not from screenreaders).
1. We want to hide content from screenreaders (but not visually).

## Hiding content for everyone

<!-- ### Usecase: -->

Common situations where you want to hide content from everyone, including people navigating by keyboard and using screenreaders are closed navigation menus, tooltip text and collapsed accordions. 

Any of the styles below will  remove the content from the visual flow of the page, will be ignored by screen readers and will prevent keyboard users tabbing to the content. 

<!-- ### Method: -->
<pre>
<code class="language-css">
{ display: none; }
</code>
</pre>

<pre>
<code class="language-css">
{ visibility: hidden; }
</code>
</pre>

<pre>
<code class="language-css">
{ width: 0px, height: 0px; }
</code>
</pre>



## Hiding content visually

There are two main situations when you want to hide content visually:

- When you _never_ want the content to be visible on the page.
- When you want the content to become visible when focused.

### Never visible

There are times when the visual information in a design is not sufficient for screen readers users. A common example of this is form inputs that aren't given visual labels. 

Labels are imperitive for screen reader users to understand and successfully complete forms. So in a situation like this you could visually hide the label with CSS. 

The most commonly accepted practice for modern browser support is using clip-rect.

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

Elements with this class would be not be visible on the page or take up any space in the visual flow. This technique is not suitable for elements that are focusable by the keyboard.

### Visble when focused

Sometimes we want to hide an element only until it recieves keyboard focus. 

A perfect example of this is [skip-links](https://webaim.org/techniques/skipnav/). A skip-link is styled with CSS to remain out of view until a user tabs to the element and then sent back out of view when it leaves focus. This behaviour benefits sighted keyboard users, for example people with mobility impairments.

<!-- ### Method - Visble when focused: -->

We use a combination of css properties to position the content offscreen and the ```:focus``` pseudo element to bring the position onto the page as the element by the keyboard.

<pre style="margin-bottom:0;">
<code class="language-css">
.skip-link a {
    position: absolute;
    left: -10000px;
    top: auto;
    width: 1px;
    height: 1px;
    overflow: hidden;
}
</code>
</pre>
<pre style="margin-top:0">
<code class="language-css">
.skip-link a:focus { 
    position: static; 
    width: auto; 
    height: auto;
}
</code>
</pre>


### Combined approach
An alternative approach is to combine these two methods and use the ```:not(:focus)``` and ```:not(:active)``` pseudo elements within the sr-only class. This will remove the hidden styling when an element is focused or active. 

<pre>
<code class="language-css">
.sr-only:not(:focus):not(:active) {
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

## Hiding content from screen readers

<!-- ### Usecase: -->

It's uncommon to need content to be hidden from screenreaders only, however this can be appropriate when visual content is decorative or duplicative. An example would be svg or font icons that are accompanied by text labels. 

We can hide the icons from assistive technology using ```aria-hidden="true"```. This effectively has the opposite behaviour of our ```sr-only``` class.

<!-- ### Method: -->

<pre>
<code class="language-markup">
&lt;button>
    &lt;span class="icon-close-menu" aria-hidden="true"></span> 
    &lt;span class="sr-only">Close navigation menu</span>
&lt;/button>
</code>
</pre>

## Further Reading

If you're interested in learning more about hiding content accessibly I've included some links to more information below:

- [Invisible Content Just For Screen Readers by WebAIM](https://webaim.org/techniques/css/invisiblecontent/)
- [How to Hide Content by The A11y Project](https://a11yproject.com/posts/how-to-hide-content/)
- [Inclusively Hidden by Scott O'Hara](https://www.scottohara.me/blog/2017/04/14/inclusively-hidden.html)

