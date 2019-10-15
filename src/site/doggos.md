---
title: Doggos
# subtitle: (Metaphorically speaking)
layout: layouts/base.njk
meta: Jess Budd is UI developer, web accessibility consultant and digital producer based in Perth, Australia. 
---

<div class="container__blog">
<div class="oldContent">

## Recent Posts

- [The Many Dog Breeds](/posts/dogs-are-the-best)
- [Why Everyone Should Own a Dog](/posts/dogs-are-the-best)
- [Caring For Your Dog](/posts/dogs-are-the-best)
- [Dogs Are The Best](/posts/dogs-are-the-best)

</div>
</div>

<script>

    var container = document.querySelector('.container__blog');
    var oldContent = document.querySelector('.oldContent');

    var link = document.querySelector('.container__blog ul');

     var newContent = document.createElement('div');
     var h1 = document.createElement('h1');
     var p = document.createElement('p');
     var img = document.createElement('img');
     img.src = '/images/dog.png'

      newContent.classList = 'newContent';


    link.addEventListener('click', function(e) {
        e.preventDefault();
        container.replaceChild(img, oldContent);
    });
    
   

  
    // console.log(newContent);

  




</script>