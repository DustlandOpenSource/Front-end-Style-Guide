Front-end Style Guide
=====================
## References
* [MDN: Writing Efficient CSS](https://developer.mozilla.org/en-US/docs/Web/Guide/CSS/Writing_efficient_CSS)
* [Google: CSS Rules Intro](https://developers.google.com/speed/docs/best-practices/rules_intro)
* [Google: Optimizing CSS](https://developers.google.com/speed/articles/optimizing-css)
* [CSS Tricks: Efficiently Rendering CSS](http://css-tricks.com/efficiently-rendering-css/)
* [AngularJs Style Guide](https://github.com/mgechev/angularjs-style-guide)

## General
##### Indent consistently and keep line length small
Version control systems compare by lines. You can often avoid merge conflicts by properly separating functions into new lines
*Bad:*
```
myObj.func1().func2().func3().css('display', 'none');
```

*Good*
```
myObj.func1()
   .func2()
   .func3()
   .css('display', 'none');
```

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

##### Avoid the descendant (child) and universal selectors.
*Very Bad:*
```
#mainMenu > li > ul > li {}
```
```
#mainMenu * {}
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

## SASS
#### Avoid deeply nested styling
Nesting is awesome! It creates structure, and add's some modularity to your styling. But nesting too deeply, especially when its not neccessary, causes LOTS issues. Use the DRY (Don't Repeat Yourself) method to avoid duplication, and only override those styles when necessary. Try to stick to 3-4 levels as a maximum. 

---
#### Avoid specifity issues by avoiding deeply nested styling
Deeply nested styling also causes specifity issues (when you have to create more classes to your styling to override the previous styling). This is easily avoided when you stick to a max of 3-4 levels deep of styling. Of course there will be times when you go over this, but its a good rule of thumb.

---
#### Don't duplicate Compass provided mixins
Get familiar with Compass and it's documentation. Search there before creating your own mixin, and you'll avoid recreating those mixins. Also, you'll probably notice that Compass' mixins are more reliable, lighter and more browser friendly that the mixin you were about to write.

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

*Optionally, going backwards typically has better performance*
```
for (var i = myArray.length; i >= 0; i--) {...}
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

##### Minimize DOM operations
*Bad:*
```
var len = 3;
	for(i =0; i <len; i++){
		$('.list').append('<li></li>')
	}
```
*Good:* 
```
	var len = 3,
		items = [];

	for(i =0; i <len; i++){
		items.push('<li></li>');
	}

	$('.list').append(items.join(''));
```

##### Use === NOT ==
*Very Bad:*
```
1 == "1"
```
*Good*
```
1 === "1"
```

##### If a script shouldnt block the page parsing process, add async to the script tag
*Bad*
```
<script src="analytics-lib.js"></script>
```

*Good*
```
<script src="analytics-lib.js" async></script>
```

## JavaScript Libraries
 
* Don’t use [jQuery](http://jquery.com/) if its not necessary.
* Use [Lo-Dash](http://lodash.com/) instead of [Underscore](http://underscorejs.org/).
