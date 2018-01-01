---
layout: post
title: Photo teszt lap
category: teszt
tags: [photo, fotó, poc, teszt, html, css]
---

<!-- break -->

Ez egy teszt oldal a képek kezeléséhez:

<button id="btn">Open PhotoSwipe</button>

<a href="javascript:openPhotoSwipe(); gallery.goTo(0);">1</a>
<a href="javascript:openPhotoSwipe();gallery.goTo(1);">2</a>
<a href="javascript:openPhotoSwipe(); gallery.goTo(0);">3</a>

<div class="row" style="margin-left: 1em;"> 
  <div class="column">
    <img src="images/1.jpg">
    <img src="images/1.jpg">
    <img src="images/1.jpg">
    <img src="images/1.jpg">
    <img src="images/1.jpg">
    <a href="javascript:openPhotoSwipe();gallery.goTo(1);"><img src="images/konyvespolc.jpg"></a>
    <img src="images/1.jpg">
  </div>
  <div class="column">
    <img src="images/5.jpg">
    <img src="images/2.jpg">
    <img src="images/2.jpg">
    <img src="images/2.jpg">
    <img src="images/2.jpg">
    <img src="images/konyvespolc.jpg">
  </div> 
  <div class="column">
    <img src="images/2.jpg">
    <img src="images/1.jpg">
    <img src="falls2.jpg">
    <img src="paris.jpg">
    <img src="images/1.jpg">
    <img src="images/konyvespolc.jpg">
    <img src="images/konyvespolc.jpg">
  </div>
  <div class="column">
    <img src="images/5.jpg">
    <img src="images/4.jpg">
    <img src="images/2.jpg">
    <img src="images/konyvespolc.jpg">
    <img src="rocks.jpg">
    <img src="underwater.jpg">
  </div>
</div>

<hr>

<div class="row" style="margin-left: 1em;"> 
  <div class="column">
    <img src="images/1.jpg">
    <img src="images/1.jpg">
    <img src="images/1.jpg">
    <img src="images/1.jpg">
    <img src="images/1.jpg">
    <a href="javascript:openPhotoSwipe();gallery.goTo(1);"><img src="images/konyvespolc.jpg"></a>
    <img src="images/1.jpg">
  </div>
  <div class="column">
    <img src="images/5.jpg">
    <img src="images/2.jpg">
    <img src="images/2.jpg">
    <img src="images/2.jpg">
    <img src="images/2.jpg">
    <img src="images/konyvespolc.jpg">
  </div> 
  <div class="column">
    <img src="images/2.jpg">
    <img src="images/1.jpg">
    <img src="falls2.jpg">
    <img src="paris.jpg">
    <img src="images/1.jpg">
    <img src="images/konyvespolc.jpg">
    <img src="images/konyvespolc.jpg">
  </div>
  <div class="column">
    <img src="images/5.jpg">
    <img src="images/4.jpg">
    <img src="images/2.jpg">
    <img src="images/konyvespolc.jpg">
    <img src="rocks.jpg">
    <img src="underwater.jpg">
  </div>
</div>

 <!-- more -->

<script type="text/javascript">

var gallery;

var openPhotoSwipe = function() {
    var pswpElement = document.querySelectorAll('.pswp')[0];

    // build items array
    var items = [
        {
            src: 'images/1.jpg',
            w: 964,
            h: 1024,
            title: 'Image Caption',
            author: 'John Doe'
        },
        {
            src: 'images/5.jpg',
            w: 1024,
            h: 683
        }
    ];
    
    // define options (if needed)
    var options = {
             // history & focus options are disabled on CodePen        
        history: false,
        focus: false,

        showAnimationDuration: 0,
        hideAnimationDuration: 0
        
    };
    
    gallery = new PhotoSwipe( pswpElement, PhotoSwipeUI_Default, items, options);
    gallery.init();
    
};


//openPhotoSwipe();
//document.getElementById('btn').onclick = openPhotoSwipe;

</script>

# Egy következő H1

és itt egy záró sor

Itt meg egy kis kód:

```javascript
var s = "JavaScript syntax highlighting";
alert(s);
```
és egy kis lista1:

 * aslaskaskla skl
 * asaksjkas ka ksaj 

és egy kis lista2:

 1. askajsjjsk
 2. asjkajsajsaks
 3. sjdksdjskdjksdjk