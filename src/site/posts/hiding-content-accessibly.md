---
title: Hiding Content Accessibly
subtitle: 
date: 2019-10-19
meta: 
# img: https://jessbudd.com/images/featured/confSpeaker.png
# tag: speaking
---

## Hiding content for everyone

## Hiding content visually

## Hiding content from screen readers



## Animating Content Challenges

Animating content can pose a tricky challenge due to the way css is applied. Many JavaScript animation libraries rely soley on hiding content by toggling opacity from 0 to 1, and giving the container a height of 0px. The issue with this implementation is the the content is still accessible to screen readers and keyboard users (if it contains focusable elements) when it should not be. 

Unfortunately, it's not as easy as swapping out the opacity for a display none. 

This is because smooth animations rely on the the content already existing in the DOM.

For this project, we were specifically using [anime.js](). Fortunately, this library allows you to add extra steps before and after a transition.  


## Further Reading

If you're interested in learning more about hiding content accessibly I've included some links to more information below:

- [Invisible Content Just For Screen Readers by WebAIM](https://webaim.org/techniques/css/invisiblecontent/)
- [How to Hide Content by The A11y Project](https://a11yproject.com/posts/how-to-hide-content/)
- [Inclusively Hidden by Scott O'Hara](https://www.scottohara.me/blog/2017/04/14/inclusively-hidden.html)

