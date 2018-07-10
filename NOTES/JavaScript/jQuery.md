# jQuery

[You Don't Need jQuery](https://github.com/nefe/You-Dont-Need-jQuery)

The jQuery library contains the following features:

- HTML/DOM manipulation

- CSS manipulation

- HTML event methods

- Effects and animations

- AJAX

- Utilities

In addition, jQuery has plugins for almost any task out there.

The jQuery team knows all about cross-browser issues, and they have written this knowledge into the jQuery library. jQuery will run exactly the same in all major browsers.

#### Importing the Script

The **integrity and crossorigin** properties in the example ensure the file is delivered without any third-party manipulation.

---

CDN

One big advantage of using the hosted jQuery from Google or Microsoft:

Many users already have downloaded jQuery from Google or Microsoft when visiting another site. As a result, it will be loaded from cache when they visit your site, which leads to faster loading time. Also, most CDN's will make sure that once a user requests a file from it, it will be served from the server closest to them, which also leads to faster loading time.

---

The jQuery syntax is tailor-made for **selecting** HTML elements and performing some **action** on the element(s).

Basic syntax is: $(selector).action()

- A $ sign to define/access jQuery

- A (selector) to "query (or find)" HTML elements

- A jQuery action() to be performed on the element(s)

---

$(this).hide() - hides the current element.

$("p").hide() - hides all <p> elements.

$(".test").hide() - hides all elements with class="test".

$("#test").hide() - hides the element with id="test".

---

This is to prevent any jQuery code from running before the document is finished loading (is ready).

It is good practice to wait for the document to be fully loaded and ready before working with it. This also allows you to have your JavaScript code before the body of your document, in the head section.

```
$(document).ready(function(){

   // jQuery methods go here...

});

// same as

$(function(){

   // jQuery methods go here...

});
```

---
