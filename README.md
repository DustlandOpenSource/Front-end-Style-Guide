Front-end Style Guide
=====================
## References
* [MDN: Writing Efficient CSS](https://developer.mozilla.org/en-US/docs/Web/Guide/CSS/Writing_efficient_CSS)
* [Google: CSS Rules Intro](https://developers.google.com/speed/docs/best-practices/rules_intro)
* [Google: Optimizing CSS](https://developers.google.com/speed/articles/optimizing-css)
* [CSS Tricks: Efficiently Rendering CSS](http://css-tricks.com/efficiently-rendering-css/)

## CSS
##### Using every declaration just once.
*Bad:*
```
h1 { color: black; }
h2 { color: black; }
h3 { color: black; }
p { color: black; }
```
*Good:*
```
h1, h2, h3, p { color: black; }
```
*Best (if applicable):*
```
body { color: black; }
```
---

##### Don’t concatenate ID’s or Classnames with tag names.
*Bad:*
```
ul#mainMenu {}
ul li.list-item {}
```
*Better:*
```
#mainMenu li {}
#mainMenu .list-item {}
ul .list-item {}
```
*Best:*
```
#mainMenu .list-item
```
---

##### Avoid the descendant (child) selector.
*Very Bad:*
```
#mainMenu > li > ul > li {}
```
---

##### Rely on inheritance.
*Bad:*
```
#mainMenu li { list-style-image: url(blah); }
```
*Good:*
```
#mainMenu { list-style-image: url(blah); }
```
---

##### Avoid vendor specific tags as much as possible.
---

## JavaScript / jQuery

#### Apply the same selectors you’d use in CSS, to JavaScript selectors.
*Bad:*
```
$(‘ul#mainMenu li’)
```
*Good:*
```
$(‘#mainMenu .list-item’)
```
*Better(use context):*
```
$(‘.list-item’, ‘#mainMenu’)
```
*Best (use find()):*
```
$(‘#mainMenu’).find(‘.list-item’)
```
---

##### Optimize loops
*Bad:*
```
$.each();
```
*Good:*
```
for (var i = 0; iLen = myArray.length; i < iLen; i++) {...}
```
---

##### Always cache selectors.
*Bad:*
```
$(‘#mainMenu .list-items’).css(‘display’, ‘none’);
$(‘#mainMenu’).on(‘hover’, function() {...});
```
*Good:*
```
var $menu = $(‘#mainMenu’);
var $menuItems = $menu.find(‘.list-items’);
$menuItems.css(‘display’, ‘none’);
$menu.on('hover', function(){...});
```
---

## JavaScript Libraries
 
* Don’t use [jQuery](http://jquery.com/) if its not necessary.
* Use [Lo-Dash](http://lodash.com/) instead of [Underscore](http://underscorejs.org/).
