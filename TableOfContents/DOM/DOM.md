
The term **elements** & **node elements** are used interchangeably but when people say the DOM is working with an element it is actually working with a node that __represents__ that element.


### Caching DOM Queries
Methods that find elements in the DOM tree are called **DOM queries**.

Note: When you need to work with an element more than once, you should use a variable to store the result of this query. This saves the browser looking through the DOM tree to find the same element(s) again. It is known as **caching** the selection. Programmers would say that the variable stores a "reference" to the object in the DOM tree (it is storing the location of the node.)

When people talk about storing elements in variables, they are really storing the location of the element(s) within the DOM tree in a variable. The properties and methods of that element node work on the variable.


The term **elements** & **node elements** are used interchangeably but when people say the DOM is working with an element it is actually working with a node that __represents__ that element.


### Caching DOM Queries
Methods that find elements in the DOM tree are called **DOM queries**.

Note: When you need to work with an element more than once, you should use a variable to store the result of this query. This saves the browser looking through the DOM tree to find the same element(s) again. It is known as **caching** the selection. Programmers would say that the variable stores a "reference" to the object in the DOM tree (it is storing the location of the node.)

When people talk about storing elements in variables, they are really storing the location of the element(s) within the DOM tree in a variable. The properties and methods of that element node work on the variable.


### Selecting an individual element node

> getElementById()
Selects an individual element given the value of its id attribute.
Note: this is always quickest and most efficient way to access an element since ID's can be repeated.

> querySelector()
Uses CSS selector syntax that would select one or more elements. This method returns only the **first** of the matching elements.


### Selecting multiple elements (known as a NodeList)

> getElementsByClassName()
Selects one or more elements given the value of their class attribute.
Note: this method is faster than querySelectorAll().

> getElementsByTagName()
Selects ALL elements on the page with a specified tag name.
Note: this method is faster than querySelectorAll().

> querySelectorAll()
Uses CSS Selector syntax to select one or more elements and returns all of those matches.

### Traversing between element nodes

parentNode

previousSibling

nextSibling

firstChild

lastChild


**NodeLists** When a DOM method **can** return more that one element, it returns a NodeList (even if it only finds one matching element). A Nodelist is a collection of element nodes. Each node is given an index number ( a number that starts at 0, just like arrays)

Note: Nodelists look like arrays and are numbered like arrays, but they are not actually arrays, they are a type of object called a **collection**.


### Live and Static NodeLists

There are times when you will want to work with the same selection of elements several times, so the NodeList can be stored in a variable and re-used  (rather than collecting the same elements again).

**Live NodeList**
When a script updates the page, the NodeList is updated at the same time. All methods starting with **getElementsBy** return a live NodeLists. Note: they are faster to generate than static NodeLists.

**Static NodeList**
When a script updates the page the node list is NOTE updated. **querySelectors** return static NodeLists. They reflect the document WHEN the query was made. If the script changes the content on the page the NodeList is NOT updated to reflect those changes.

###### Breaking down all four parts of the DOM selection method below:

```
document.getElementById('one')
```

**document** --> Refers to the document object. You always have to access individual elements via the document object.

**. (member operator)** --> The dot notation indicates that the method (on the right) is being applied to the node on the left side of the period.

**method** --> The getElementById() method indicates that you want to find the element based upon the value of its ID attribute.

**parameter** --> The method needs to know the value of the id attribute on the element you want. It is the parameter of the method.


### the item() Method

There are two ways to select an element form a NodeList:

1. the item() method
> var firstItem = elements.item(0);

2. array syntax
> var firstItem = elements[0];

Note: Array syntax is preferred over the item() method because it is faster. Before selecting a node form a NodeList, check that is contains nodes. If you repeatedly use the NodeList, store it in a variable.

### Steps for DOM selecting/updating

1. Find the element nodes
```
var elements = document.getElementsByClassName("soccer"); // finds "soccer" elements
```

2. conditional (optional)
```
if (elements.length > 2) { // if 3 or more are found
}
```

3. Select (inside if statement in this example )
```
var el = elements[2] // selects the third element in the NodeList
```

4. Update/change value (inside if statement in this example)
```
el.className = "basketball";
```


### Repeating actions for an entire NodeList.

```
var hotItems = document.querySelectorAll('li.hot');
for (var i = 0; i < hotItems.length; i++) {
    hotItems[i].className = 'cool';
}
```
1. The variable hotItems contains a NodeList.
It contains all list items whose class attribue has a value of "hot".
They are colleted using the querySelectorAll() method.

2. The length property of the NodeList indicates how many elements are in the NodeList.
The number of elements dictates how many times the loop should run.

3. Array syntax is used to indicate which item in the NodeList is currently being wordked with: hotItems[i]
It used the counter variable inside the sqaure brackets.

### Set Attribute
```
var fistItem.setAttribute('class', 'soccer');
```

Note: When an element contains a mix of text and other elements, you are more likely to work with the containing element rahter than the individual nodes for each descendant.

Add: How to deal with Whitespace Nodes.


##### Update this section of the DOM notes next.

**The Document Object Model - DOM**
The only purpose of the html is for the browser to ingest it  and turn it into the DOM, if you want to some nothing with it after then you can manipulate it via the DOM API. HTML is parsed into a DOM " a string to a tree" that string is rendered to the DOM so it displays a certain way. Every web browser has something called the DOM, where DOM is an acronym for Document Object Model. The DOM is an API, where API is an acronym for Application Programming Interface. Simply put, an API is a way for programs to interact with each-other.

> Write JavaScript against the DOM API
    * Includes event handlers for clicks, key events, submit events
    * Creates and appends DOM elements
    * Uses event delegation to capture events from dynamically added elements
    * Finds existing elements by id and className in order to make changes
    * Mutates properties on existing DOM elements such as style, classNames

> Target, create, and manipulate DOM Elements
    * Creates and appends DOM elements
    * Finds existing elements by id and className in order to make changes
    * Mutates properties on existing DOM elements such as style, classNames

**DOM Elements | Node Tree**
How the DOM models the document:

The DOM models (represents) the document as an object.Objects are nice because programs can interact with them easily. It would be hard if we had to interact with the document by having our programs read the HTML or use computer vision to interact with the browser window. This isn't just any object, it is a special data structure known as a tree. The data structure gets its name because it can be visually represented to look like a real world tree: a tree has a trunk, the trunk has branches, each branch can have more branches. The data structure tree has a root node (trunk), the root node has nodes (branches), a node (branch) can have other nodes (branches). The file system is a tree. The root directory / is the root node (trunk). It contains several other directories, each of these is a node (branch). Each of those directories contain other directories (nodes).


Just like a directory:
* A node contained in another node is known as the child node.
* A node that contains another node is known as the parent node.

How the HTML maps to the tree:
1. The <html></html> tag becomes the root node.
2. It has 2 child nodes: <head></head>, <body></body
3. The <head></head> node has a child node: <title></title>.
4. The <body></body> node has 2 child nodes: <h1></h1>, <div></div>.
5. The <div></div> node has a child node: <p></p>.


**Selection/Traversal**

querySelector(“ “) - only returns the first match.
querySelectorAll(“ “) - returns the selected “nodelist”

firstChild & lastChild - example: selecting the first and/or last node. (li’s inside a ul)
parentNode & childNode - example: selecting the ul would be the parentNode of an li (which would be considered the childNode)
previousSibling & nextSibling - adjacent node elements on the same level, example li’s that are next to each other.
nodeValue is a little more confusing to use, but faster than innerHTML
innerHTML parses content as HTML and takes longer.
textContent uses straight text, does not parse HTML, and is faster.
innerText Takes styles into consideration. It won't get hidden text for instance.
createElement -
createTextNode -
removeChild -
appendChild -
.setAttribute -
type this is the name of the event
target (node) - this is the dom node where the event originated.
preventDefault - (function) This prevents any default behavior from occurring that the user agent (i.e. browser) might carry out in relation to the event (for example, preventing a click event on an <a> element from loading a new page).
load event:  fires on any resource that has finished loading (including any dependent resources). This could be an image, stylesheet, script, video, audio file, document or window.

Form Validation
New.js ← example form file

function getFormData() {
This selects all form inputs by queryselector
 var data = new FormData(document.querySelector("#submittedForm"));
This collects all the form data
function getFormData() {
This selects all form inputs by queryselector
 var data = new FormData(document.querySelector("#submittedForm"));

Returns the data from the form itself? For this return the "name:" is the data that it is getting and "nameInput" is the "name" that is on the actual form field itself.
 return {
       name: data.get("nameInput"),
       city: data.get("cityInput"),
       state: data.get("stateInput"),
       country: data.get("countryInput"),
       division: data.get("divisionInput"),
 };
}
   .then(response => response.json())
   .then(response => {
     // log
     console.log(response);
   }).catch(console.error);
}


Events
Events: actions or occurrences that happen in the system you are programming, which the system tells you amour so you can respond to them in some way if desired. For example if the user clicks a button on a webpage you mights what to respond to that action by displaying info.
Click Event: common DOM event fired by the browser when you click on something with your mouse.
Event Handler: the "onclick" handler property is equal to an anonymous function which contains the code we want the click event to run.
document.querySelector ("html").onclick - function () {};
(is equivalent to)
var myHTML = document.querySelector("html");
myHTML.onclick = function() {};


Inline event handlers (do NOT use)
<button onclick="bgChange()"> Press Me </button>
function bgChange() {
var newColor……
document.body.style.backgroundColor = bgChange;
}

addEventListener() / removeEventListener: functions similar way to the event handler properties but the syntax is different.
var btn = document.querySelector("button");
function bgChange() {
// some code
}
btn.addEventListener("click", bgChange);


Event Handler vs add/removeEventListener: Event handler properties have less power and options, but better cross browser compatibility. While add/removeEventListener are more powerful, but can also become more complex and are less supported by browsers. The main advantage to using add/removeEventListener is that you can add multiple listeners to the same type of element if required. You can also call these on an element multiple times with different functions specified in the second argument(they scale better) This would be impossible with event handler properties because any subsequent attempts to set a property will overwrite the earlier ones.
element.addEventListener(<event-name>, <callback>, <use-capture>);
event-name (string) This is the name or type of event that you would like to listen to. It could be any of the standard DOM events (click, mousedown, touchstart, transitionEnd, etc.) or even your own custom event name (we’ll touch on custom events later).
callback (function) This function gets called when the event happens. The event object, containing data about the event, is passed as the first argument.
* use-capture (boolean) This declares whether the callback should be fired in the “capture” phase.

Event Objects: inside of event handler functions you might see a parameter specified with a name such as event, eve, or e. This is called an event object and is automatically passed to the event handler to provide extra features and information.

function bgChange(e) {
    var newColor
     // some code
     console.log(e);
}
btn.addEventListener("click", bgChange);

The term **elements** & **node elements** are used interchangeably but when people say the DOM is working with an element it is actually working with a node that __represents__ that element.


### Caching DOM Queries
Methods that find elements in the DOM tree are called **DOM queries**.

Note: When you need to work with an element more than once, you should use a variable to store the result of this query. This saves the browser looking through the DOM tree to find the same element(s) again. It is known as **caching** the selection. Programmers would say that the variable stores a "reference" to the object in the DOM tree (it is storing the location of the node.)

When people talk about storing elements in variables, they are really storing the location of the element(s) within the DOM tree in a variable. The properties and methods of that element node work on the variable.


### Selecting an individual element node

> getElementById()
Selects an individual element given the value of its id attribute.
Note: this is always quickest and most efficient way to access an element since ID's can be repeated.

> querySelector()
Uses CSS selector syntax that would select one or more elements. This method returns only the **first** of the matching elements.


### Selecting multiple elements (known as a NodeList)

> getElementsByClassName()
Selects one or more elements given the value of their class attribute.
Note: this method is faster than querySelectorAll().

> getElementsByTagName()
Selects ALL elements on the page with a specified tag name.
Note: this method is faster than querySelectorAll().

> querySelectorAll()
Uses CSS Selector syntax to select one or more elements and returns all of those matches.

### Traversing between element nodes

parentNode

previousSibling

nextSibling

firstChild

lastChild


**NodeLists** When a DOM method **can** return more that one element, it returns a NodeList (even if it only finds one matching element). A Nodelist is a collection of element nodes. Each node is given an index number ( a number that starts at 0, just like arrays)

Note: Nodelists look like arrays and are numbered like arrays, but they are not actually arrays, they are a type of object called a **collection**.


### Live and Static NodeLists

There are times when you will want to work with the same selection of elements several times, so the NodeList can be stored in a variable and re-used  (rather than collecting the same elements again).

**Live NodeList**
When a script updates the page, the NodeList is updated at the same time. All methods starting with **getElementsBy** return a live NodeLists. Note: they are faster to generate than static NodeLists.

**Static NodeList**
When a script updates the page the node list is NOTE updated. **querySelectors** return static NodeLists. They reflect the document WHEN the query was made. If the script changes the content on the page the NodeList is NOT updated to reflect those changes.

###### Breaking down all four parts of the DOM selection method below:

```
document.getElementById('one')
```

**document** --> Refers to the document object. You always have to access individual elements via the document object.

**. (member operator)** --> The dot notation indicates that the method (on the right) is being applied to the node on the left side of the period.

**method** --> The getElementById() method indicates that you want to find the element based upon the value of its ID attribute.

**parameter** --> The method needs to know the value of the id attribute on the element you want. It is the parameter of the method.


### the item() Method

There are two ways to select an element form a NodeList:

1. the item() method
> var firstItem = elements.item(0);

2. array syntax
> var firstItem = elements[0];

Note: Array syntax is preferred over the item() method because it is faster. Before selecting a node form a NodeList, check that is contains nodes. If you repeatedly use the NodeList, store it in a variable.

### Steps for DOM selecting/updating

1. Find the element nodes
```
var elements = document.getElementsByClassName("soccer"); // finds "soccer" elements
```

2. conditional (optional)
```
if (elements.length > 2) { // if 3 or more are found
}
```

3. Select (inside if statement in this example )
```
var el = elements[2] // selects the third element in the NodeList
```

4. Update/change value (inside if statement in this example)
```
el.className = "basketball";
```


##### Update this section of the DOM notes next.

**The Document Object Model - DOM**
The only purpose of the html is for the browser to ingest it  and turn it into the DOM, if you want to some nothing with it after then you can manipulate it via the DOM API. HTML is parsed into a DOM " a string to a tree" that string is rendered to the DOM so it displays a certain way. Every web browser has something called the DOM, where DOM is an acronym for Document Object Model. The DOM is an API, where API is an acronym for Application Programming Interface. Simply put, an API is a way for programs to interact with each-other.

> Write JavaScript against the DOM API
    * Includes event handlers for clicks, key events, submit events
    * Creates and appends DOM elements
    * Uses event delegation to capture events from dynamically added elements
    * Finds existing elements by id and className in order to make changes
    * Mutates properties on existing DOM elements such as style, classNames

> Target, create, and manipulate DOM Elements
    * Creates and appends DOM elements
    * Finds existing elements by id and className in order to make changes
    * Mutates properties on existing DOM elements such as style, classNames

**DOM Elements | Node Tree**
How the DOM models the document:

The DOM models (represents) the document as an object.Objects are nice because programs can interact with them easily. It would be hard if we had to interact with the document by having our programs read the HTML or use computer vision to interact with the browser window. This isn't just any object, it is a special data structure known as a tree. The data structure gets its name because it can be visually represented to look like a real world tree: a tree has a trunk, the trunk has branches, each branch can have more branches. The data structure tree has a root node (trunk), the root node has nodes (branches), a node (branch) can have other nodes (branches). The file system is a tree. The root directory / is the root node (trunk). It contains several other directories, each of these is a node (branch). Each of those directories contain other directories (nodes).


Just like a directory:
* A node contained in another node is known as the child node.
* A node that contains another node is known as the parent node.

How the HTML maps to the tree:
1. The <html></html> tag becomes the root node.
2. It has 2 child nodes: <head></head>, <body></body
3. The <head></head> node has a child node: <title></title>.
4. The <body></body> node has 2 child nodes: <h1></h1>, <div></div>.
5. The <div></div> node has a child node: <p></p>.


**Selection/Traversal**

querySelector(“ “) - only returns the first match.
querySelectorAll(“ “) - returns the selected “nodelist”

firstChild & lastChild - example: selecting the first and/or last node. (li’s inside a ul)
parentNode & childNode - example: selecting the ul would be the parentNode of an li (which would be considered the childNode)
previousSibling & nextSibling - adjacent node elements on the same level, example li’s that are next to each other.
nodeValue is a little more confusing to use, but faster than innerHTML
innerHTML parses content as HTML and takes longer.
textContent uses straight text, does not parse HTML, and is faster.
innerText Takes styles into consideration. It won't get hidden text for instance.
createElement -
createTextNode -
removeChild -
appendChild -
.setAttribute -
type this is the name of the event
target (node) - this is the dom node where the event originated.
preventDefault - (function) This prevents any default behavior from occurring that the user agent (i.e. browser) might carry out in relation to the event (for example, preventing a click event on an <a> element from loading a new page).
load event:  fires on any resource that has finished loading (including any dependent resources). This could be an image, stylesheet, script, video, audio file, document or window.

Form Validation
New.js ← example form file

function getFormData() {
This selects all form inputs by queryselector
 var data = new FormData(document.querySelector("#submittedForm"));
This collects all the form data
function getFormData() {
This selects all form inputs by queryselector
 var data = new FormData(document.querySelector("#submittedForm"));

Returns the data from the form itself? For this return the "name:" is the data that it is getting and "nameInput" is the "name" that is on the actual form field itself.
 return {
       name: data.get("nameInput"),
       city: data.get("cityInput"),
       state: data.get("stateInput"),
       country: data.get("countryInput"),
       division: data.get("divisionInput"),
 };
}
   .then(response => response.json())
   .then(response => {
     // log
     console.log(response);
   }).catch(console.error);
}


Events
Events: actions or occurrences that happen in the system you are programming, which the system tells you amour so you can respond to them in some way if desired. For example if the user clicks a button on a webpage you mights what to respond to that action by displaying info.
Click Event: common DOM event fired by the browser when you click on something with your mouse.
Event Handler: the "onclick" handler property is equal to an anonymous function which contains the code we want the click event to run.
document.querySelector ("html").onclick - function () {};
(is equivalent to)
var myHTML = document.querySelector("html");
myHTML.onclick = function() {};


Inline event handlers (do NOT use)
<button onclick="bgChange()"> Press Me </button>
function bgChange() {
var newColor……
document.body.style.backgroundColor = bgChange;
}

addEventListener() / removeEventListener: functions similar way to the event handler properties but the syntax is different.
var btn = document.querySelector("button");
function bgChange() {
// some code
}
btn.addEventListener("click", bgChange);


Event Handler vs add/removeEventListener: Event handler properties have less power and options, but better cross browser compatibility. While add/removeEventListener are more powerful, but can also become more complex and are less supported by browsers. The main advantage to using add/removeEventListener is that you can add multiple listeners to the same type of element if required. You can also call these on an element multiple times with different functions specified in the second argument(they scale better) This would be impossible with event handler properties because any subsequent attempts to set a property will overwrite the earlier ones.
element.addEventListener(<event-name>, <callback>, <use-capture>);
event-name (string) This is the name or type of event that you would like to listen to. It could be any of the standard DOM events (click, mousedown, touchstart, transitionEnd, etc.) or even your own custom event name (we’ll touch on custom events later).
callback (function) This function gets called when the event happens. The event object, containing data about the event, is passed as the first argument.
* use-capture (boolean) This declares whether the callback should be fired in the “capture” phase.

Event Objects: inside of event handler functions you might see a parameter specified with a name such as event, eve, or e. This is called an event object and is automatically passed to the event handler to provide extra features and information.

function bgChange(e) {
    var newColor
     // some code
     console.log(e);
}
btn.addEventListener("click", bgChange);


Event Delegation & Bubbling: Bubbling allows us to take advantage of event delegation. This concept relies on the fact that id you want code to run when you clock any one of a large number of child elements, you can set the event listener on their parent and have the effect of the event listener bubble to each child, rather than having to set the event listener on every child individually. A good example is a series of listed items - if you want each one to "pop up" with a message when clicked, you can set the click event listener on the the parent ur and it will bubble to the list items.
Event Delegation: You can trigger an event on a parent by clicking on a child element for example.
Event Bubbling Visual Demo: https://codepen.io/BertoOrt/pen/GmmarX
<ul> - adding the click event listener to the ul will "bubble" down and apply to all the li's.
     <li> test </li>
 <li> test </li>
</ul>


The term **elements** & **node elements** are used interchangeably but when people say the DOM is working with an element it is actually working with a node that __represents__ that element.


### Caching DOM Queries
Methods that find elements in the DOM tree are called **DOM queries**.

Note: When you need to work with an element more than once, you should use a variable to store the result of this query. This saves the browser looking through the DOM tree to find the same element(s) again. It is known as **caching** the selection. Programmers would say that the variable stores a "reference" to the object in the DOM tree (it is storing the location of the node.)

When people talk about storing elements in variables, they are really storing the location of the element(s) within the DOM tree in a variable. The properties and methods of that element node work on the variable.


### Selecting an individual element node

> getElementById()
Selects an individual element given the value of its id attribute.
Note: this is always quickest and most efficient way to access an element since ID's can be repeated.

> querySelector()
Uses CSS selector syntax that would select one or more elements. This method returns only the **first** of the matching elements.


### Selecting multiple elements (known as a NodeList)

> getElementsByClassName()
Selects one or more elements given the value of their class attribute.
Note: this method is faster than querySelectorAll().

> getElementsByTagName()
Selects ALL elements on the page with a specified tag name.
Note: this method is faster than querySelectorAll().

> querySelectorAll()
Uses CSS Selector syntax to select one or more elements and returns all of those matches.

### Traversing between element nodes

parentNode

previousSibling

nextSibling

firstChild

lastChild


**NodeLists** When a DOM method **can** return more that one element, it returns a NodeList (even if it only finds one matching element). A Nodelist is a collection of element nodes. Each node is given an index number ( a number that starts at 0, just like arrays)

Note: Nodelists look like arrays and are numbered like arrays, but they are not actually arrays, they are a type of object called a **collection**.


### Live and Static NodeLists

There are times when you will want to work with the same selection of elements several times, so the NodeList can be stored in a variable and re-used  (rather than collecting the same elements again).

**Live NodeList**
When a script updates the page, the NodeList is updated at the same time. All methods starting with **getElementsBy** return a live NodeLists. Note: they are faster to generate than static NodeLists.

**Static NodeList**
When a script updates the page the node list is NOTE updated. **querySelectors** return static NodeLists. They reflect the document WHEN the query was made. If the script changes the content on the page the NodeList is NOT updated to reflect those changes.

###### Breaking down all four parts of the DOM selection method below:

```
document.getElementById('one')
```

**document** --> Refers to the document object. You always have to access individual elements via the document object.

**. (member operator)** --> The dot notation indicates that the method (on the right) is being applied to the node on the left side of the period.

**method** --> The getElementById() method indicates that you want to find the element based upon the value of its ID attribute.

**parameter** --> The method needs to know the value of the id attribute on the element you want. It is the parameter of the method.


### the item() Method

There are two ways to select an element form a NodeList:

1. the item() method
> var firstItem = elements.item(0);

2. array syntax
> var firstItem = elements[0];

Note: Array syntax is preferred over the item() method because it is faster. Before selecting a node form a NodeList, check that is contains nodes. If you repeatedly use the NodeList, store it in a variable.

### Steps for DOM selecting/updating

1. Find the element nodes
```
var elements = document.getElementsByClassName("soccer"); // finds "soccer" elements
```

2. conditional (optional)
```
if (elements.length > 2) { // if 3 or more are found
}
```

3. Select (inside if statement in this example )
```
var el = elements[2] // selects the third element in the NodeList
```

4. Update/change value (inside if statement in this example)
```
el.className = "basketball";
```


##### Update this section of the DOM notes next.

**The Document Object Model - DOM**
The only purpose of the html is for the browser to ingest it  and turn it into the DOM, if you want to some nothing with it after then you can manipulate it via the DOM API. HTML is parsed into a DOM " a string to a tree" that string is rendered to the DOM so it displays a certain way. Every web browser has something called the DOM, where DOM is an acronym for Document Object Model. The DOM is an API, where API is an acronym for Application Programming Interface. Simply put, an API is a way for programs to interact with each-other.

> Write JavaScript against the DOM API
    * Includes event handlers for clicks, key events, submit events
    * Creates and appends DOM elements
    * Uses event delegation to capture events from dynamically added elements
    * Finds existing elements by id and className in order to make changes
    * Mutates properties on existing DOM elements such as style, classNames

> Target, create, and manipulate DOM Elements
    * Creates and appends DOM elements
    * Finds existing elements by id and className in order to make changes
    * Mutates properties on existing DOM elements such as style, classNames

**DOM Elements | Node Tree**
How the DOM models the document:

The DOM models (represents) the document as an object.Objects are nice because programs can interact with them easily. It would be hard if we had to interact with the document by having our programs read the HTML or use computer vision to interact with the browser window. This isn't just any object, it is a special data structure known as a tree. The data structure gets its name because it can be visually represented to look like a real world tree: a tree has a trunk, the trunk has branches, each branch can have more branches. The data structure tree has a root node (trunk), the root node has nodes (branches), a node (branch) can have other nodes (branches). The file system is a tree. The root directory / is the root node (trunk). It contains several other directories, each of these is a node (branch). Each of those directories contain other directories (nodes).


Just like a directory:
* A node contained in another node is known as the child node.
* A node that contains another node is known as the parent node.

How the HTML maps to the tree:
1. The <html></html> tag becomes the root node.
2. It has 2 child nodes: <head></head>, <body></body
3. The <head></head> node has a child node: <title></title>.
4. The <body></body> node has 2 child nodes: <h1></h1>, <div></div>.
5. The <div></div> node has a child node: <p></p>.


**Selection/Traversal**

querySelector(“ “) - only returns the first match.
querySelectorAll(“ “) - returns the selected “nodelist”

firstChild & lastChild - example: selecting the first and/or last node. (li’s inside a ul)
parentNode & childNode - example: selecting the ul would be the parentNode of an li (which would be considered the childNode)
previousSibling & nextSibling - adjacent node elements on the same level, example li’s that are next to each other.
nodeValue is a little more confusing to use, but faster than innerHTML
innerHTML parses content as HTML and takes longer.
textContent uses straight text, does not parse HTML, and is faster.
innerText Takes styles into consideration. It won't get hidden text for instance.
createElement -
createTextNode -
removeChild -
appendChild -
.setAttribute -
type this is the name of the event
target (node) - this is the dom node where the event originated.
preventDefault - (function) This prevents any default behavior from occurring that the user agent (i.e. browser) might carry out in relation to the event (for example, preventing a click event on an <a> element from loading a new page).
load event:  fires on any resource that has finished loading (including any dependent resources). This could be an image, stylesheet, script, video, audio file, document or window.

Form Validation
New.js ← example form file

function getFormData() {
This selects all form inputs by queryselector
 var data = new FormData(document.querySelector("#submittedForm"));
This collects all the form data
function getFormData() {
This selects all form inputs by queryselector
 var data = new FormData(document.querySelector("#submittedForm"));

Returns the data from the form itself? For this return the "name:" is the data that it is getting and "nameInput" is the "name" that is on the actual form field itself.
 return {
       name: data.get("nameInput"),
       city: data.get("cityInput"),
       state: data.get("stateInput"),
       country: data.get("countryInput"),
       division: data.get("divisionInput"),
 };
}
   .then(response => response.json())
   .then(response => {
     // log
     console.log(response);
   }).catch(console.error);
}


Events
Events: actions or occurrences that happen in the system you are programming, which the system tells you amour so you can respond to them in some way if desired. For example if the user clicks a button on a webpage you mights what to respond to that action by displaying info.
Click Event: common DOM event fired by the browser when you click on something with your mouse.
Event Handler: the "onclick" handler property is equal to an anonymous function which contains the code we want the click event to run.
document.querySelector ("html").onclick - function () {};
(is equivalent to)
var myHTML = document.querySelector("html");
myHTML.onclick = function() {};


Inline event handlers (do NOT use)
<button onclick="bgChange()"> Press Me </button>
function bgChange() {
var newColor……
document.body.style.backgroundColor = bgChange;
}

addEventListener() / removeEventListener: functions similar way to the event handler properties but the syntax is different.
var btn = document.querySelector("button");
function bgChange() {
// some code
}
btn.addEventListener("click", bgChange);


Event Handler vs add/removeEventListener: Event handler properties have less power and options, but better cross browser compatibility. While add/removeEventListener are more powerful, but can also become more complex and are less supported by browsers. The main advantage to using add/removeEventListener is that you can add multiple listeners to the same type of element if required. You can also call these on an element multiple times with different functions specified in the second argument(they scale better) This would be impossible with event handler properties because any subsequent attempts to set a property will overwrite the earlier ones.
element.addEventListener(<event-name>, <callback>, <use-capture>);
event-name (string) This is the name or type of event that you would like to listen to. It could be any of the standard DOM events (click, mousedown, touchstart, transitionEnd, etc.) or even your own custom event name (we’ll touch on custom events later).
callback (function) This function gets called when the event happens. The event object, containing data about the event, is passed as the first argument.
* use-capture (boolean) This declares whether the callback should be fired in the “capture” phase.

Event Objects: inside of event handler functions you might see a parameter specified with a name such as event, eve, or e. This is called an event object and is automatically passed to the event handler to provide extra features and information.

function bgChange(e) {
    var newColor
     // some code
     console.log(e);
}
btn.addEventListener("click", bgChange);


Event Delegation & Bubbling: Bubbling allows us to take advantage of event delegation. This concept relies on the fact that id you want code to run when you clock any one of a large number of child elements, you can set the event listener on their parent and have the effect of the event listener bubble to each child, rather than having to set the event listener on every child individually. A good example is a series of listed items - if you want each one to "pop up" with a message when clicked, you can set the click event listener on the the parent ur and it will bubble to the list items.
Event Delegation: You can trigger an event on a parent by clicking on a child element for example.
Event Bubbling Visual Demo: https://codepen.io/BertoOrt/pen/GmmarX
<ul> - adding the click event listener to the ul will "bubble" down and apply to all the li's.
     <li> test </li>
 <li> test </li>
</ul>


The term **elements** & **node elements** are used interchangeably but when people say the DOM is working with an element it is actually working with a node that __represents__ that element.


### Caching DOM Queries
Methods that find elements in the DOM tree are called **DOM queries**.

Note: When you need to work with an element more than once, you should use a variable to store the result of this query. This saves the browser looking through the DOM tree to find the same element(s) again. It is known as **caching** the selection. Programmers would say that the variable stores a "reference" to the object in the DOM tree (it is storing the location of the node.)

When people talk about storing elements in variables, they are really storing the location of the element(s) within the DOM tree in a variable. The properties and methods of that element node work on the variable.


### Selecting an individual element node

> getElementById()
Selects an individual element given the value of its id attribute.
Note: this is always quickest and most efficient way to access an element since ID's can be repeated.

> querySelector()
Uses CSS selector syntax that would select one or more elements. This method returns only the **first** of the matching elements.


### Selecting multiple elements (known as a NodeList)

> getElementsByClassName()
Selects one or more elements given the value of their class attribute.
Note: this method is faster than querySelectorAll().

> getElementsByTagName()
Selects ALL elements on the page with a specified tag name.
Note: this method is faster than querySelectorAll().

> querySelectorAll()
Uses CSS Selector syntax to select one or more elements and returns all of those matches.

### Traversing between element nodes

parentNode

previousSibling

nextSibling

firstChild

lastChild


**NodeLists** When a DOM method **can** return more that one element, it returns a NodeList (even if it only finds one matching element). A Nodelist is a collection of element nodes. Each node is given an index number ( a number that starts at 0, just like arrays)

Note: Nodelists look like arrays and are numbered like arrays, but they are not actually arrays, they are a type of object called a **collection**.


### Live and Static NodeLists

There are times when you will want to work with the same selection of elements several times, so the NodeList can be stored in a variable and re-used  (rather than collecting the same elements again).

**Live NodeList**
When a script updates the page, the NodeList is updated at the same time. All methods starting with **getElementsBy** return a live NodeLists. Note: they are faster to generate than static NodeLists.

**Static NodeList**
When a script updates the page the node list is NOTE updated. **querySelectors** return static NodeLists. They reflect the document WHEN the query was made. If the script changes the content on the page the NodeList is NOT updated to reflect those changes.

###### Breaking down all four parts of the DOM selection method below:

```
document.getElementById('one')
```

**document** --> Refers to the document object. You always have to access individual elements via the document object.

**. (member operator)** --> The dot notation indicates that the method (on the right) is being applied to the node on the left side of the period.

**method** --> The getElementById() method indicates that you want to find the element based upon the value of its ID attribute.

**parameter** --> The method needs to know the value of the id attribute on the element you want. It is the parameter of the method.


### the item() Method

There are two ways to select an element form a NodeList:

1. the item() method
> var firstItem = elements.item(0);

2. array syntax
> var firstItem = elements[0];

Note: Array syntax is preferred over the item() method because it is faster. Before selecting a node form a NodeList, check that is contains nodes. If you repeatedly use the NodeList, store it in a variable.

### Steps for DOM selecting/updating

1. Find the element nodes
```
var elements = document.getElementsByClassName("soccer"); // finds "soccer" elements
```

2. conditional (optional)
```
if (elements.length > 2) { // if 3 or more are found
}
```

3. Select (inside if statement in this example )
```
var el = elements[2] // selects the third element in the NodeList
```

4. Update/change value (inside if statement in this example)
```
el.className = "basketball";
```


##### Update this section of the DOM notes next.

**The Document Object Model - DOM**
The only purpose of the html is for the browser to ingest it  and turn it into the DOM, if you want to some nothing with it after then you can manipulate it via the DOM API. HTML is parsed into a DOM " a string to a tree" that string is rendered to the DOM so it displays a certain way. Every web browser has something called the DOM, where DOM is an acronym for Document Object Model. The DOM is an API, where API is an acronym for Application Programming Interface. Simply put, an API is a way for programs to interact with each-other.

> Write JavaScript against the DOM API
    * Includes event handlers for clicks, key events, submit events
    * Creates and appends DOM elements
    * Uses event delegation to capture events from dynamically added elements
    * Finds existing elements by id and className in order to make changes
    * Mutates properties on existing DOM elements such as style, classNames

> Target, create, and manipulate DOM Elements
    * Creates and appends DOM elements
    * Finds existing elements by id and className in order to make changes
    * Mutates properties on existing DOM elements such as style, classNames

**DOM Elements | Node Tree**
How the DOM models the document:

The DOM models (represents) the document as an object.Objects are nice because programs can interact with them easily. It would be hard if we had to interact with the document by having our programs read the HTML or use computer vision to interact with the browser window. This isn't just any object, it is a special data structure known as a tree. The data structure gets its name because it can be visually represented to look like a real world tree: a tree has a trunk, the trunk has branches, each branch can have more branches. The data structure tree has a root node (trunk), the root node has nodes (branches), a node (branch) can have other nodes (branches). The file system is a tree. The root directory / is the root node (trunk). It contains several other directories, each of these is a node (branch). Each of those directories contain other directories (nodes).


Just like a directory:
* A node contained in another node is known as the child node.
* A node that contains another node is known as the parent node.

How the HTML maps to the tree:
1. The <html></html> tag becomes the root node.
2. It has 2 child nodes: <head></head>, <body></body
3. The <head></head> node has a child node: <title></title>.
4. The <body></body> node has 2 child nodes: <h1></h1>, <div></div>.
5. The <div></div> node has a child node: <p></p>.


**Selection/Traversal**

querySelector(“ “) - only returns the first match.
querySelectorAll(“ “) - returns the selected “nodelist”

firstChild & lastChild - example: selecting the first and/or last node. (li’s inside a ul)
parentNode & childNode - example: selecting the ul would be the parentNode of an li (which would be considered the childNode)
previousSibling & nextSibling - adjacent node elements on the same level, example li’s that are next to each other.
nodeValue is a little more confusing to use, but faster than innerHTML
innerHTML parses content as HTML and takes longer.
textContent uses straight text, does not parse HTML, and is faster.
innerText Takes styles into consideration. It won't get hidden text for instance.
createElement -
createTextNode -
removeChild -
appendChild -
.setAttribute -
type this is the name of the event
target (node) - this is the dom node where the event originated.
preventDefault - (function) This prevents any default behavior from occurring that the user agent (i.e. browser) might carry out in relation to the event (for example, preventing a click event on an <a> element from loading a new page).
load event:  fires on any resource that has finished loading (including any dependent resources). This could be an image, stylesheet, script, video, audio file, document or window.

Form Validation
New.js ← example form file

function getFormData() {
This selects all form inputs by queryselector
 var data = new FormData(document.querySelector("#submittedForm"));
This collects all the form data
function getFormData() {
This selects all form inputs by queryselector
 var data = new FormData(document.querySelector("#submittedForm"));

Returns the data from the form itself? For this return the "name:" is the data that it is getting and "nameInput" is the "name" that is on the actual form field itself.
 return {
       name: data.get("nameInput"),
       city: data.get("cityInput"),
       state: data.get("stateInput"),
       country: data.get("countryInput"),
       division: data.get("divisionInput"),
 };
}
   .then(response => response.json())
   .then(response => {
     // log
     console.log(response);
   }).catch(console.error);
}


Events
Events: actions or occurrences that happen in the system you are programming, which the system tells you amour so you can respond to them in some way if desired. For example if the user clicks a button on a webpage you mights what to respond to that action by displaying info.
Click Event: common DOM event fired by the browser when you click on something with your mouse.
Event Handler: the "onclick" handler property is equal to an anonymous function which contains the code we want the click event to run.
document.querySelector ("html").onclick - function () {};
(is equivalent to)
var myHTML = document.querySelector("html");
myHTML.onclick = function() {};


Inline event handlers (do NOT use)
<button onclick="bgChange()"> Press Me </button>
function bgChange() {
var newColor……
document.body.style.backgroundColor = bgChange;
}

addEventListener() / removeEventListener: functions similar way to the event handler properties but the syntax is different.
var btn = document.querySelector("button");
function bgChange() {
// some code
}
btn.addEventListener("click", bgChange);


Event Handler vs add/removeEventListener: Event handler properties have less power and options, but better cross browser compatibility. While add/removeEventListener are more powerful, but can also become more complex and are less supported by browsers. The main advantage to using add/removeEventListener is that you can add multiple listeners to the same type of element if required. You can also call these on an element multiple times with different functions specified in the second argument(they scale better) This would be impossible with event handler properties because any subsequent attempts to set a property will overwrite the earlier ones.
element.addEventListener(<event-name>, <callback>, <use-capture>);
event-name (string) This is the name or type of event that you would like to listen to. It could be any of the standard DOM events (click, mousedown, touchstart, transitionEnd, etc.) or even your own custom event name (we’ll touch on custom events later).
callback (function) This function gets called when the event happens. The event object, containing data about the event, is passed as the first argument.
* use-capture (boolean) This declares whether the callback should be fired in the “capture” phase.

Event Objects: inside of event handler functions you might see a parameter specified with a name such as event, eve, or e. This is called an event object and is automatically passed to the event handler to provide extra features and information.

function bgChange(e) {
    var newColor
     // some code
     console.log(e);
}
btn.addEventListener("click", bgChange);


Event Delegation & Bubbling: Bubbling allows us to take advantage of event delegation. This concept relies on the fact that id you want code to run when you clock any one of a large number of child elements, you can set the event listener on their parent and have the effect of the event listener bubble to each child, rather than having to set the event listener on every child individually. A good example is a series of listed items - if you want each one to "pop up" with a message when clicked, you can set the click event listener on the the parent ur and it will bubble to the list items.
Event Delegation: You can trigger an event on a parent by clicking on a child element for example.
Event Bubbling Visual Demo: https://codepen.io/BertoOrt/pen/GmmarX
<ul> - adding the click event listener to the ul will "bubble" down and apply to all the li's.
     <li> test </li>
 <li> test </li>
</ul>


The term **elements** & **node elements** are used interchangeably but when people say the DOM is working with an element it is actually working with a node that __represents__ that element.


### Caching DOM Queries
Methods that find elements in the DOM tree are called **DOM queries**.

Note: When you need to work with an element more than once, you should use a variable to store the result of this query. This saves the browser looking through the DOM tree to find the same element(s) again. It is known as **caching** the selection. Programmers would say that the variable stores a "reference" to the object in the DOM tree (it is storing the location of the node.)

When people talk about storing elements in variables, they are really storing the location of the element(s) within the DOM tree in a variable. The properties and methods of that element node work on the variable.


### Selecting an individual element node

> getElementById()
Selects an individual element given the value of its id attribute.
Note: this is always quickest and most efficient way to access an element since ID's can be repeated.

> querySelector()
Uses CSS selector syntax that would select one or more elements. This method returns only the **first** of the matching elements.


### Selecting multiple elements (known as a NodeList)

> getElementsByClassName()
Selects one or more elements given the value of their class attribute.
Note: this method is faster than querySelectorAll().

> getElementsByTagName()
Selects ALL elements on the page with a specified tag name.
Note: this method is faster than querySelectorAll().

> querySelectorAll()
Uses CSS Selector syntax to select one or more elements and returns all of those matches.

### Traversing between element nodes

parentNode

previousSibling

nextSibling

firstChild

lastChild


**NodeLists** When a DOM method **can** return more that one element, it returns a NodeList (even if it only finds one matching element). A Nodelist is a collection of element nodes. Each node is given an index number ( a number that starts at 0, just like arrays)

Note: Nodelists look like arrays and are numbered like arrays, but they are not actually arrays, they are a type of object called a **collection**.


### Live and Static NodeLists

There are times when you will want to work with the same selection of elements several times, so the NodeList can be stored in a variable and re-used  (rather than collecting the same elements again).

**Live NodeList**
When a script updates the page, the NodeList is updated at the same time. All methods starting with **getElementsBy** return a live NodeLists. Note: they are faster to generate than static NodeLists.

**Static NodeList**
When a script updates the page the node list is NOTE updated. **querySelectors** return static NodeLists. They reflect the document WHEN the query was made. If the script changes the content on the page the NodeList is NOT updated to reflect those changes.

###### Breaking down all four parts of the DOM selection method below:

```
document.getElementById('one')
```

**document** --> Refers to the document object. You always have to access individual elements via the document object.

**. (member operator)** --> The dot notation indicates that the method (on the right) is being applied to the node on the left side of the period.

**method** --> The getElementById() method indicates that you want to find the element based upon the value of its ID attribute.

**parameter** --> The method needs to know the value of the id attribute on the element you want. It is the parameter of the method.


### the item() Method

There are two ways to select an element form a NodeList:

1. the item() method
> var firstItem = elements.item(0);

2. array syntax
> var firstItem = elements[0];

Note: Array syntax is preferred over the item() method because it is faster. Before selecting a node form a NodeList, check that is contains nodes. If you repeatedly use the NodeList, store it in a variable.

### Steps for DOM selecting/updating

1. Find the element nodes
```
var elements = document.getElementsByClassName("soccer"); // finds "soccer" elements
```

2. conditional (optional)
```
if (elements.length > 2) { // if 3 or more are found
}
```

3. Select (inside if statement in this example )
```
var el = elements[2] // selects the third element in the NodeList
```

4. Update/change value (inside if statement in this example)
```
el.className = "basketball";
```


##### Update this section of the DOM notes next.

**The Document Object Model - DOM**
The only purpose of the html is for the browser to ingest it  and turn it into the DOM, if you want to some nothing with it after then you can manipulate it via the DOM API. HTML is parsed into a DOM " a string to a tree" that string is rendered to the DOM so it displays a certain way. Every web browser has something called the DOM, where DOM is an acronym for Document Object Model. The DOM is an API, where API is an acronym for Application Programming Interface. Simply put, an API is a way for programs to interact with each-other.

> Write JavaScript against the DOM API
    * Includes event handlers for clicks, key events, submit events
    * Creates and appends DOM elements
    * Uses event delegation to capture events from dynamically added elements
    * Finds existing elements by id and className in order to make changes
    * Mutates properties on existing DOM elements such as style, classNames

> Target, create, and manipulate DOM Elements
    * Creates and appends DOM elements
    * Finds existing elements by id and className in order to make changes
    * Mutates properties on existing DOM elements such as style, classNames

**DOM Elements | Node Tree**
How the DOM models the document:

The DOM models (represents) the document as an object.Objects are nice because programs can interact with them easily. It would be hard if we had to interact with the document by having our programs read the HTML or use computer vision to interact with the browser window. This isn't just any object, it is a special data structure known as a tree. The data structure gets its name because it can be visually represented to look like a real world tree: a tree has a trunk, the trunk has branches, each branch can have more branches. The data structure tree has a root node (trunk), the root node has nodes (branches), a node (branch) can have other nodes (branches). The file system is a tree. The root directory / is the root node (trunk). It contains several other directories, each of these is a node (branch). Each of those directories contain other directories (nodes).


Just like a directory:
* A node contained in another node is known as the child node.
* A node that contains another node is known as the parent node.

How the HTML maps to the tree:
1. The <html></html> tag becomes the root node.
2. It has 2 child nodes: <head></head>, <body></body
3. The <head></head> node has a child node: <title></title>.
4. The <body></body> node has 2 child nodes: <h1></h1>, <div></div>.
5. The <div></div> node has a child node: <p></p>.


**Selection/Traversal**

querySelector(“ “) - only returns the first match.
querySelectorAll(“ “) - returns the selected “nodelist”

firstChild & lastChild - example: selecting the first and/or last node. (li’s inside a ul)
parentNode & childNode - example: selecting the ul would be the parentNode of an li (which would be considered the childNode)
previousSibling & nextSibling - adjacent node elements on the same level, example li’s that are next to each other.
nodeValue is a little more confusing to use, but faster than innerHTML
innerHTML parses content as HTML and takes longer.
textContent uses straight text, does not parse HTML, and is faster.
innerText Takes styles into consideration. It won't get hidden text for instance.
createElement -
createTextNode -
removeChild -
appendChild -
.setAttribute -
type this is the name of the event
target (node) - this is the dom node where the event originated.
preventDefault - (function) This prevents any default behavior from occurring that the user agent (i.e. browser) might carry out in relation to the event (for example, preventing a click event on an <a> element from loading a new page).
load event:  fires on any resource that has finished loading (including any dependent resources). This could be an image, stylesheet, script, video, audio file, document or window.

Form Validation
New.js ← example form file

function getFormData() {
This selects all form inputs by queryselector
 var data = new FormData(document.querySelector("#submittedForm"));
This collects all the form data
function getFormData() {
This selects all form inputs by queryselector
 var data = new FormData(document.querySelector("#submittedForm"));

Returns the data from the form itself? For this return the "name:" is the data that it is getting and "nameInput" is the "name" that is on the actual form field itself.
 return {
       name: data.get("nameInput"),
       city: data.get("cityInput"),
       state: data.get("stateInput"),
       country: data.get("countryInput"),
       division: data.get("divisionInput"),
 };
}
   .then(response => response.json())
   .then(response => {
     // log
     console.log(response);
   }).catch(console.error);
}


Events
Events: actions or occurrences that happen in the system you are programming, which the system tells you amour so you can respond to them in some way if desired. For example if the user clicks a button on a webpage you mights what to respond to that action by displaying info.
Click Event: common DOM event fired by the browser when you click on something with your mouse.
Event Handler: the "onclick" handler property is equal to an anonymous function which contains the code we want the click event to run.
document.querySelector ("html").onclick - function () {};
(is equivalent to)
var myHTML = document.querySelector("html");
myHTML.onclick = function() {};


Inline event handlers (do NOT use)
<button onclick="bgChange()"> Press Me </button>
function bgChange() {
var newColor……
document.body.style.backgroundColor = bgChange;
}

addEventListener() / removeEventListener: functions similar way to the event handler properties but the syntax is different.
var btn = document.querySelector("button");
function bgChange() {
// some code
}
btn.addEventListener("click", bgChange);


Event Handler vs add/removeEventListener: Event handler properties have less power and options, but better cross browser compatibility. While add/removeEventListener are more powerful, but can also become more complex and are less supported by browsers. The main advantage to using add/removeEventListener is that you can add multiple listeners to the same type of element if required. You can also call these on an element multiple times with different functions specified in the second argument(they scale better) This would be impossible with event handler properties because any subsequent attempts to set a property will overwrite the earlier ones.
element.addEventListener(<event-name>, <callback>, <use-capture>);
event-name (string) This is the name or type of event that you would like to listen to. It could be any of the standard DOM events (click, mousedown, touchstart, transitionEnd, etc.) or even your own custom event name (we’ll touch on custom events later).
callback (function) This function gets called when the event happens. The event object, containing data about the event, is passed as the first argument.
* use-capture (boolean) This declares whether the callback should be fired in the “capture” phase.

Event Objects: inside of event handler functions you might see a parameter specified with a name such as event, eve, or e. This is called an event object and is automatically passed to the event handler to provide extra features and information.

function bgChange(e) {
    var newColor
     // some code
     console.log(e);
}
btn.addEventListener("click", bgChange);


Event Delegation & Bubbling: Bubbling allows us to take advantage of event delegation. This concept relies on the fact that id you want code to run when you clock any one of a large number of child elements, you can set the event listener on their parent and have the effect of the event listener bubble to each child, rather than having to set the event listener on every child individually. A good example is a series of listed items - if you want each one to "pop up" with a message when clicked, you can set the click event listener on the the parent ur and it will bubble to the list items.
Event Delegation: You can trigger an event on a parent by clicking on a child element for example.
Event Bubbling Visual Demo: https://codepen.io/BertoOrt/pen/GmmarX
<ul> - adding the click event listener to the ul will "bubble" down and apply to all the li's.
     <li> test </li>
 <li> test </li>
</ul>


The term **elements** & **node elements** are used interchangeably but when people say the DOM is working with an element it is actually working with a node that __represents__ that element.


### Caching DOM Queries
Methods that find elements in the DOM tree are called **DOM queries**.

Note: When you need to work with an element more than once, you should use a variable to store the result of this query. This saves the browser looking through the DOM tree to find the same element(s) again. It is known as **caching** the selection. Programmers would say that the variable stores a "reference" to the object in the DOM tree (it is storing the location of the node.)

When people talk about storing elements in variables, they are really storing the location of the element(s) within the DOM tree in a variable. The properties and methods of that element node work on the variable.


### Selecting an individual element node

> getElementById()
Selects an individual element given the value of its id attribute.
Note: this is always quickest and most efficient way to access an element since ID's can be repeated.

> querySelector()
Uses CSS selector syntax that would select one or more elements. This method returns only the **first** of the matching elements.


### Selecting multiple elements (known as a NodeList)

> getElementsByClassName()
Selects one or more elements given the value of their class attribute.
Note: this method is faster than querySelectorAll().

> getElementsByTagName()
Selects ALL elements on the page with a specified tag name.
Note: this method is faster than querySelectorAll().

> querySelectorAll()
Uses CSS Selector syntax to select one or more elements and returns all of those matches.

### Traversing between element nodes

parentNode

previousSibling

nextSibling

firstChild

lastChild


**NodeLists** When a DOM method **can** return more that one element, it returns a NodeList (even if it only finds one matching element). A Nodelist is a collection of element nodes. Each node is given an index number ( a number that starts at 0, just like arrays)

Note: Nodelists look like arrays and are numbered like arrays, but they are not actually arrays, they are a type of object called a **collection**.


### Live and Static NodeLists

There are times when you will want to work with the same selection of elements several times, so the NodeList can be stored in a variable and re-used  (rather than collecting the same elements again).

**Live NodeList**
When a script updates the page, the NodeList is updated at the same time. All methods starting with **getElementsBy** return a live NodeLists. Note: they are faster to generate than static NodeLists.

**Static NodeList**
When a script updates the page the node list is NOTE updated. **querySelectors** return static NodeLists. They reflect the document WHEN the query was made. If the script changes the content on the page the NodeList is NOT updated to reflect those changes.

###### Breaking down all four parts of the DOM selection method below:

```
document.getElementById('one')
```

**document** --> Refers to the document object. You always have to access individual elements via the document object.

**. (member operator)** --> The dot notation indicates that the method (on the right) is being applied to the node on the left side of the period.

**method** --> The getElementById() method indicates that you want to find the element based upon the value of its ID attribute.

**parameter** --> The method needs to know the value of the id attribute on the element you want. It is the parameter of the method.


### the item() Method

There are two ways to select an element form a NodeList:

1. the item() method
> var firstItem = elements.item(0);

2. array syntax
> var firstItem = elements[0];

Note: Array syntax is preferred over the item() method because it is faster. Before selecting a node form a NodeList, check that is contains nodes. If you repeatedly use the NodeList, store it in a variable.

### Steps for DOM selecting/updating

1. Find the element nodes
```
var elements = document.getElementsByClassName("soccer"); // finds "soccer" elements
```

2. conditional (optional)
```
if (elements.length > 2) { // if 3 or more are found
}
```

3. Select (inside if statement in this example )
```
var el = elements[2] // selects the third element in the NodeList
```

4. Update/change value (inside if statement in this example)
```
el.className = "basketball";
```


##### Update this section of the DOM notes next.

**The Document Object Model - DOM**
The only purpose of the html is for the browser to ingest it  and turn it into the DOM, if you want to some nothing with it after then you can manipulate it via the DOM API. HTML is parsed into a DOM " a string to a tree" that string is rendered to the DOM so it displays a certain way. Every web browser has something called the DOM, where DOM is an acronym for Document Object Model. The DOM is an API, where API is an acronym for Application Programming Interface. Simply put, an API is a way for programs to interact with each-other.

> Write JavaScript against the DOM API
    * Includes event handlers for clicks, key events, submit events
    * Creates and appends DOM elements
    * Uses event delegation to capture events from dynamically added elements
    * Finds existing elements by id and className in order to make changes
    * Mutates properties on existing DOM elements such as style, classNames

> Target, create, and manipulate DOM Elements
    * Creates and appends DOM elements
    * Finds existing elements by id and className in order to make changes
    * Mutates properties on existing DOM elements such as style, classNames

**DOM Elements | Node Tree**
How the DOM models the document:

The DOM models (represents) the document as an object.Objects are nice because programs can interact with them easily. It would be hard if we had to interact with the document by having our programs read the HTML or use computer vision to interact with the browser window. This isn't just any object, it is a special data structure known as a tree. The data structure gets its name because it can be visually represented to look like a real world tree: a tree has a trunk, the trunk has branches, each branch can have more branches. The data structure tree has a root node (trunk), the root node has nodes (branches), a node (branch) can have other nodes (branches). The file system is a tree. The root directory / is the root node (trunk). It contains several other directories, each of these is a node (branch). Each of those directories contain other directories (nodes).


Just like a directory:
* A node contained in another node is known as the child node.
* A node that contains another node is known as the parent node.

How the HTML maps to the tree:
1. The <html></html> tag becomes the root node.
2. It has 2 child nodes: <head></head>, <body></body
3. The <head></head> node has a child node: <title></title>.
4. The <body></body> node has 2 child nodes: <h1></h1>, <div></div>.
5. The <div></div> node has a child node: <p></p>.


**Selection/Traversal**

querySelector(“ “) - only returns the first match.
querySelectorAll(“ “) - returns the selected “nodelist”

firstChild & lastChild - example: selecting the first and/or last node. (li’s inside a ul)
parentNode & childNode - example: selecting the ul would be the parentNode of an li (which would be considered the childNode)
previousSibling & nextSibling - adjacent node elements on the same level, example li’s that are next to each other.
nodeValue is a little more confusing to use, but faster than innerHTML
innerHTML parses content as HTML and takes longer.
textContent uses straight text, does not parse HTML, and is faster.
innerText Takes styles into consideration. It won't get hidden text for instance.
createElement -
createTextNode -
removeChild -
appendChild -
.setAttribute -
type this is the name of the event
target (node) - this is the dom node where the event originated.
preventDefault - (function) This prevents any default behavior from occurring that the user agent (i.e. browser) might carry out in relation to the event (for example, preventing a click event on an <a> element from loading a new page).
load event:  fires on any resource that has finished loading (including any dependent resources). This could be an image, stylesheet, script, video, audio file, document or window.

Form Validation
New.js ← example form file

function getFormData() {
This selects all form inputs by queryselector
 var data = new FormData(document.querySelector("#submittedForm"));
This collects all the form data
function getFormData() {
This selects all form inputs by queryselector
 var data = new FormData(document.querySelector("#submittedForm"));

Returns the data from the form itself? For this return the "name:" is the data that it is getting and "nameInput" is the "name" that is on the actual form field itself.
 return {
       name: data.get("nameInput"),
       city: data.get("cityInput"),
       state: data.get("stateInput"),
       country: data.get("countryInput"),
       division: data.get("divisionInput"),
 };
}
   .then(response => response.json())
   .then(response => {
     // log
     console.log(response);
   }).catch(console.error);
}


Events
Events: actions or occurrences that happen in the system you are programming, which the system tells you amour so you can respond to them in some way if desired. For example if the user clicks a button on a webpage you mights what to respond to that action by displaying info.
Click Event: common DOM event fired by the browser when you click on something with your mouse.
Event Handler: the "onclick" handler property is equal to an anonymous function which contains the code we want the click event to run.
document.querySelector ("html").onclick - function () {};
(is equivalent to)
var myHTML = document.querySelector("html");
myHTML.onclick = function() {};


Inline event handlers (do NOT use)
<button onclick="bgChange()"> Press Me </button>
function bgChange() {
var newColor……
document.body.style.backgroundColor = bgChange;
}

addEventListener() / removeEventListener: functions similar way to the event handler properties but the syntax is different.
var btn = document.querySelector("button");
function bgChange() {
// some code
}
btn.addEventListener("click", bgChange);


Event Handler vs add/removeEventListener: Event handler properties have less power and options, but better cross browser compatibility. While add/removeEventListener are more powerful, but can also become more complex and are less supported by browsers. The main advantage to using add/removeEventListener is that you can add multiple listeners to the same type of element if required. You can also call these on an element multiple times with different functions specified in the second argument(they scale better) This would be impossible with event handler properties because any subsequent attempts to set a property will overwrite the earlier ones.
element.addEventListener(<event-name>, <callback>, <use-capture>);
event-name (string) This is the name or type of event that you would like to listen to. It could be any of the standard DOM events (click, mousedown, touchstart, transitionEnd, etc.) or even your own custom event name (we’ll touch on custom events later).
callback (function) This function gets called when the event happens. The event object, containing data about the event, is passed as the first argument.
* use-capture (boolean) This declares whether the callback should be fired in the “capture” phase.

Event Objects: inside of event handler functions you might see a parameter specified with a name such as event, eve, or e. This is called an event object and is automatically passed to the event handler to provide extra features and information.

function bgChange(e) {
    var newColor
     // some code
     console.log(e);
}
btn.addEventListener("click", bgChange);


Event Delegation & Bubbling: Bubbling allows us to take advantage of event delegation. This concept relies on the fact that id you want code to run when you clock any one of a large number of child elements, you can set the event listener on their parent and have the effect of the event listener bubble to each child, rather than having to set the event listener on every child individually. A good example is a series of listed items - if you want each one to "pop up" with a message when clicked, you can set the click event listener on the the parent ur and it will bubble to the list items.
Event Delegation: You can trigger an event on a parent by clicking on a child element for example.
Event Bubbling Visual Demo: https://codepen.io/BertoOrt/pen/GmmarX
<ul> - adding the click event listener to the ul will "bubble" down and apply to all the li's.
     <li> test </li>
 <li> test </li>
</ul>


The term **elements** & **node elements** are used interchangeably but when people say the DOM is working with an element it is actually working with a node that __represents__ that element.


### Caching DOM Queries
Methods that find elements in the DOM tree are called **DOM queries**.

Note: When you need to work with an element more than once, you should use a variable to store the result of this query. This saves the browser looking through the DOM tree to find the same element(s) again. It is known as **caching** the selection. Programmers would say that the variable stores a "reference" to the object in the DOM tree (it is storing the location of the node.)

When people talk about storing elements in variables, they are really storing the location of the element(s) within the DOM tree in a variable. The properties and methods of that element node work on the variable.


### Selecting an individual element node

> getElementById()
Selects an individual element given the value of its id attribute.
Note: this is always quickest and most efficient way to access an element since ID's can be repeated.

> querySelector()
Uses CSS selector syntax that would select one or more elements. This method returns only the **first** of the matching elements.


### Selecting multiple elements (known as a NodeList)

> getElementsByClassName()
Selects one or more elements given the value of their class attribute.
Note: this method is faster than querySelectorAll().

> getElementsByTagName()
Selects ALL elements on the page with a specified tag name.
Note: this method is faster than querySelectorAll().

> querySelectorAll()
Uses CSS Selector syntax to select one or more elements and returns all of those matches.

### Traversing between element nodes

parentNode

previousSibling

nextSibling

firstChild

lastChild


**NodeLists** When a DOM method **can** return more that one element, it returns a NodeList (even if it only finds one matching element). A Nodelist is a collection of element nodes. Each node is given an index number ( a number that starts at 0, just like arrays)

Note: Nodelists look like arrays and are numbered like arrays, but they are not actually arrays, they are a type of object called a **collection**.


### Live and Static NodeLists

There are times when you will want to work with the same selection of elements several times, so the NodeList can be stored in a variable and re-used  (rather than collecting the same elements again).

**Live NodeList**
When a script updates the page, the NodeList is updated at the same time. All methods starting with **getElementsBy** return a live NodeLists. Note: they are faster to generate than static NodeLists.

**Static NodeList**
When a script updates the page the node list is NOTE updated. **querySelectors** return static NodeLists. They reflect the document WHEN the query was made. If the script changes the content on the page the NodeList is NOT updated to reflect those changes.

###### Breaking down all four parts of the DOM selection method below:

```
document.getElementById('one')
```

**document** --> Refers to the document object. You always have to access individual elements via the document object.

**. (member operator)** --> The dot notation indicates that the method (on the right) is being applied to the node on the left side of the period.

**method** --> The getElementById() method indicates that you want to find the element based upon the value of its ID attribute.

**parameter** --> The method needs to know the value of the id attribute on the element you want. It is the parameter of the method.


### the item() Method

There are two ways to select an element form a NodeList:

1. the item() method
> var firstItem = elements.item(0);

2. array syntax
> var firstItem = elements[0];

Note: Array syntax is preferred over the item() method because it is faster. Before selecting a node form a NodeList, check that is contains nodes. If you repeatedly use the NodeList, store it in a variable.

### Steps for DOM selecting/updating

1. Find the element nodes
```
var elements = document.getElementsByClassName("soccer"); // finds "soccer" elements
```

2. conditional (optional)
```
if (elements.length > 2) { // if 3 or more are found
}
```

3. Select (inside if statement in this example )
```
var el = elements[2] // selects the third element in the NodeList
```

4. Update/change value (inside if statement in this example)
```
el.className = "basketball";
```


##### Update this section of the DOM notes next.

**The Document Object Model - DOM**
The only purpose of the html is for the browser to ingest it  and turn it into the DOM, if you want to some nothing with it after then you can manipulate it via the DOM API. HTML is parsed into a DOM " a string to a tree" that string is rendered to the DOM so it displays a certain way. Every web browser has something called the DOM, where DOM is an acronym for Document Object Model. The DOM is an API, where API is an acronym for Application Programming Interface. Simply put, an API is a way for programs to interact with each-other.

> Write JavaScript against the DOM API
    * Includes event handlers for clicks, key events, submit events
    * Creates and appends DOM elements
    * Uses event delegation to capture events from dynamically added elements
    * Finds existing elements by id and className in order to make changes
    * Mutates properties on existing DOM elements such as style, classNames

> Target, create, and manipulate DOM Elements
    * Creates and appends DOM elements
    * Finds existing elements by id and className in order to make changes
    * Mutates properties on existing DOM elements such as style, classNames

**DOM Elements | Node Tree**
How the DOM models the document:

The DOM models (represents) the document as an object.Objects are nice because programs can interact with them easily. It would be hard if we had to interact with the document by having our programs read the HTML or use computer vision to interact with the browser window. This isn't just any object, it is a special data structure known as a tree. The data structure gets its name because it can be visually represented to look like a real world tree: a tree has a trunk, the trunk has branches, each branch can have more branches. The data structure tree has a root node (trunk), the root node has nodes (branches), a node (branch) can have other nodes (branches). The file system is a tree. The root directory / is the root node (trunk). It contains several other directories, each of these is a node (branch). Each of those directories contain other directories (nodes).


Just like a directory:
* A node contained in another node is known as the child node.
* A node that contains another node is known as the parent node.

How the HTML maps to the tree:
1. The <html></html> tag becomes the root node.
2. It has 2 child nodes: <head></head>, <body></body
3. The <head></head> node has a child node: <title></title>.
4. The <body></body> node has 2 child nodes: <h1></h1>, <div></div>.
5. The <div></div> node has a child node: <p></p>.


**Selection/Traversal**

querySelector(“ “) - only returns the first match.
querySelectorAll(“ “) - returns the selected “nodelist”

firstChild & lastChild - example: selecting the first and/or last node. (li’s inside a ul)
parentNode & childNode - example: selecting the ul would be the parentNode of an li (which would be considered the childNode)
previousSibling & nextSibling - adjacent node elements on the same level, example li’s that are next to each other.
nodeValue is a little more confusing to use, but faster than innerHTML
innerHTML parses content as HTML and takes longer.
textContent uses straight text, does not parse HTML, and is faster.
innerText Takes styles into consideration. It won't get hidden text for instance.
createElement -
createTextNode -
removeChild -
appendChild -
.setAttribute -
type this is the name of the event
target (node) - this is the dom node where the event originated.
preventDefault - (function) This prevents any default behavior from occurring that the user agent (i.e. browser) might carry out in relation to the event (for example, preventing a click event on an <a> element from loading a new page).
load event:  fires on any resource that has finished loading (including any dependent resources). This could be an image, stylesheet, script, video, audio file, document or window.

Form Validation
New.js ← example form file

function getFormData() {
This selects all form inputs by queryselector
 var data = new FormData(document.querySelector("#submittedForm"));
This collects all the form data
function getFormData() {
This selects all form inputs by queryselector
 var data = new FormData(document.querySelector("#submittedForm"));

Returns the data from the form itself? For this return the "name:" is the data that it is getting and "nameInput" is the "name" that is on the actual form field itself.
 return {
       name: data.get("nameInput"),
       city: data.get("cityInput"),
       state: data.get("stateInput"),
       country: data.get("countryInput"),
       division: data.get("divisionInput"),
 };
}
   .then(response => response.json())
   .then(response => {
     // log
     console.log(response);
   }).catch(console.error);
}


Events
Events: actions or occurrences that happen in the system you are programming, which the system tells you amour so you can respond to them in some way if desired. For example if the user clicks a button on a webpage you mights what to respond to that action by displaying info.
Click Event: common DOM event fired by the browser when you click on something with your mouse.
Event Handler: the "onclick" handler property is equal to an anonymous function which contains the code we want the click event to run.
document.querySelector ("html").onclick - function () {};
(is equivalent to)
var myHTML = document.querySelector("html");
myHTML.onclick = function() {};


Inline event handlers (do NOT use)
<button onclick="bgChange()"> Press Me </button>
function bgChange() {
var newColor……
document.body.style.backgroundColor = bgChange;
}

addEventListener() / removeEventListener: functions similar way to the event handler properties but the syntax is different.
var btn = document.querySelector("button");
function bgChange() {
// some code
}
btn.addEventListener("click", bgChange);


Event Handler vs add/removeEventListener: Event handler properties have less power and options, but better cross browser compatibility. While add/removeEventListener are more powerful, but can also become more complex and are less supported by browsers. The main advantage to using add/removeEventListener is that you can add multiple listeners to the same type of element if required. You can also call these on an element multiple times with different functions specified in the second argument(they scale better) This would be impossible with event handler properties because any subsequent attempts to set a property will overwrite the earlier ones.
element.addEventListener(<event-name>, <callback>, <use-capture>);
event-name (string) This is the name or type of event that you would like to listen to. It could be any of the standard DOM events (click, mousedown, touchstart, transitionEnd, etc.) or even your own custom event name (we’ll touch on custom events later).
callback (function) This function gets called when the event happens. The event object, containing data about the event, is passed as the first argument.
* use-capture (boolean) This declares whether the callback should be fired in the “capture” phase.

Event Objects: inside of event handler functions you might see a parameter specified with a name such as event, eve, or e. This is called an event object and is automatically passed to the event handler to provide extra features and information.

function bgChange(e) {
    var newColor
     // some code
     console.log(e);
}
btn.addEventListener("click", bgChange);


Event Delegation & Bubbling: Bubbling allows us to take advantage of event delegation. This concept relies on the fact that id you want code to run when you clock any one of a large number of child elements, you can set the event listener on their parent and have the effect of the event listener bubble to each child, rather than having to set the event listener on every child individually. A good example is a series of listed items - if you want each one to "pop up" with a message when clicked, you can set the click event listener on the the parent ur and it will bubble to the list items.
Event Delegation: You can trigger an event on a parent by clicking on a child element for example.
Event Bubbling Visual Demo: https://codepen.io/BertoOrt/pen/GmmarX
<ul> - adding the click event listener to the ul will "bubble" down and apply to all the li's.
     <li> test </li>
 <li> test </li>
</ul>


The term **elements** & **node elements** are used interchangeably but when people say the DOM is working with an element it is actually working with a node that __represents__ that element.


### Caching DOM Queries
Methods that find elements in the DOM tree are called **DOM queries**.

Note: When you need to work with an element more than once, you should use a variable to store the result of this query. This saves the browser looking through the DOM tree to find the same element(s) again. It is known as **caching** the selection. Programmers would say that the variable stores a "reference" to the object in the DOM tree (it is storing the location of the node.)

When people talk about storing elements in variables, they are really storing the location of the element(s) within the DOM tree in a variable. The properties and methods of that element node work on the variable.


### Selecting an individual element node

> getElementById()
Selects an individual element given the value of its id attribute.
Note: this is always quickest and most efficient way to access an element since ID's can be repeated.

> querySelector()
Uses CSS selector syntax that would select one or more elements. This method returns only the **first** of the matching elements.


### Selecting multiple elements (known as a NodeList)

> getElementsByClassName()
Selects one or more elements given the value of their class attribute.
Note: this method is faster than querySelectorAll().

> getElementsByTagName()
Selects ALL elements on the page with a specified tag name.
Note: this method is faster than querySelectorAll().

> querySelectorAll()
Uses CSS Selector syntax to select one or more elements and returns all of those matches.

### Traversing between element nodes

parentNode

previousSibling

nextSibling

firstChild

lastChild


**NodeLists** When a DOM method **can** return more that one element, it returns a NodeList (even if it only finds one matching element). A Nodelist is a collection of element nodes. Each node is given an index number ( a number that starts at 0, just like arrays)

Note: Nodelists look like arrays and are numbered like arrays, but they are not actually arrays, they are a type of object called a **collection**.


### Live and Static NodeLists

There are times when you will want to work with the same selection of elements several times, so the NodeList can be stored in a variable and re-used  (rather than collecting the same elements again).

**Live NodeList**
When a script updates the page, the NodeList is updated at the same time. All methods starting with **getElementsBy** return a live NodeLists. Note: they are faster to generate than static NodeLists.

**Static NodeList**
When a script updates the page the node list is NOTE updated. **querySelectors** return static NodeLists. They reflect the document WHEN the query was made. If the script changes the content on the page the NodeList is NOT updated to reflect those changes.

###### Breaking down all four parts of the DOM selection method below:

```
document.getElementById('one')
```

**document** --> Refers to the document object. You always have to access individual elements via the document object.

**. (member operator)** --> The dot notation indicates that the method (on the right) is being applied to the node on the left side of the period.

**method** --> The getElementById() method indicates that you want to find the element based upon the value of its ID attribute.

**parameter** --> The method needs to know the value of the id attribute on the element you want. It is the parameter of the method.


### the item() Method

There are two ways to select an element form a NodeList:

1. the item() method
> var firstItem = elements.item(0);

2. array syntax
> var firstItem = elements[0];

Note: Array syntax is preferred over the item() method because it is faster. Before selecting a node form a NodeList, check that is contains nodes. If you repeatedly use the NodeList, store it in a variable.

### Steps for DOM selecting/updating

1. Find the element nodes
```
var elements = document.getElementsByClassName("soccer"); // finds "soccer" elements
```

2. conditional (optional)
```
if (elements.length > 2) { // if 3 or more are found
}
```

3. Select (inside if statement in this example )
```
var el = elements[2] // selects the third element in the NodeList
```

4. Update/change value (inside if statement in this example)
```
el.className = "basketball";
```


##### Update this section of the DOM notes next.

**The Document Object Model - DOM**
The only purpose of the html is for the browser to ingest it  and turn it into the DOM, if you want to some nothing with it after then you can manipulate it via the DOM API. HTML is parsed into a DOM " a string to a tree" that string is rendered to the DOM so it displays a certain way. Every web browser has something called the DOM, where DOM is an acronym for Document Object Model. The DOM is an API, where API is an acronym for Application Programming Interface. Simply put, an API is a way for programs to interact with each-other.

> Write JavaScript against the DOM API
    * Includes event handlers for clicks, key events, submit events
    * Creates and appends DOM elements
    * Uses event delegation to capture events from dynamically added elements
    * Finds existing elements by id and className in order to make changes
    * Mutates properties on existing DOM elements such as style, classNames

> Target, create, and manipulate DOM Elements
    * Creates and appends DOM elements
    * Finds existing elements by id and className in order to make changes
    * Mutates properties on existing DOM elements such as style, classNames

**DOM Elements | Node Tree**
How the DOM models the document:

The DOM models (represents) the document as an object.Objects are nice because programs can interact with them easily. It would be hard if we had to interact with the document by having our programs read the HTML or use computer vision to interact with the browser window. This isn't just any object, it is a special data structure known as a tree. The data structure gets its name because it can be visually represented to look like a real world tree: a tree has a trunk, the trunk has branches, each branch can have more branches. The data structure tree has a root node (trunk), the root node has nodes (branches), a node (branch) can have other nodes (branches). The file system is a tree. The root directory / is the root node (trunk). It contains several other directories, each of these is a node (branch). Each of those directories contain other directories (nodes).


Just like a directory:
* A node contained in another node is known as the child node.
* A node that contains another node is known as the parent node.

How the HTML maps to the tree:
1. The <html></html> tag becomes the root node.
2. It has 2 child nodes: <head></head>, <body></body
3. The <head></head> node has a child node: <title></title>.
4. The <body></body> node has 2 child nodes: <h1></h1>, <div></div>.
5. The <div></div> node has a child node: <p></p>.


**Selection/Traversal**

querySelector(“ “) - only returns the first match.
querySelectorAll(“ “) - returns the selected “nodelist”

firstChild & lastChild - example: selecting the first and/or last node. (li’s inside a ul)
parentNode & childNode - example: selecting the ul would be the parentNode of an li (which would be considered the childNode)
previousSibling & nextSibling - adjacent node elements on the same level, example li’s that are next to each other.
nodeValue is a little more confusing to use, but faster than innerHTML
innerHTML parses content as HTML and takes longer.
textContent uses straight text, does not parse HTML, and is faster.
innerText Takes styles into consideration. It won't get hidden text for instance.
createElement -
createTextNode -
removeChild -
appendChild -
.setAttribute -
type this is the name of the event
target (node) - this is the dom node where the event originated.
preventDefault - (function) This prevents any default behavior from occurring that the user agent (i.e. browser) might carry out in relation to the event (for example, preventing a click event on an <a> element from loading a new page).
load event:  fires on any resource that has finished loading (including any dependent resources). This could be an image, stylesheet, script, video, audio file, document or window.

Form Validation
New.js ← example form file

function getFormData() {
This selects all form inputs by queryselector
 var data = new FormData(document.querySelector("#submittedForm"));
This collects all the form data
function getFormData() {
This selects all form inputs by queryselector
 var data = new FormData(document.querySelector("#submittedForm"));

Returns the data from the form itself? For this return the "name:" is the data that it is getting and "nameInput" is the "name" that is on the actual form field itself.
 return {
       name: data.get("nameInput"),
       city: data.get("cityInput"),
       state: data.get("stateInput"),
       country: data.get("countryInput"),
       division: data.get("divisionInput"),
 };
}
   .then(response => response.json())
   .then(response => {
     // log
     console.log(response);
   }).catch(console.error);
}


Events
Events: actions or occurrences that happen in the system you are programming, which the system tells you amour so you can respond to them in some way if desired. For example if the user clicks a button on a webpage you mights what to respond to that action by displaying info.
Click Event: common DOM event fired by the browser when you click on something with your mouse.
Event Handler: the "onclick" handler property is equal to an anonymous function which contains the code we want the click event to run.
document.querySelector ("html").onclick - function () {};
(is equivalent to)
var myHTML = document.querySelector("html");
myHTML.onclick = function() {};


Inline event handlers (do NOT use)
<button onclick="bgChange()"> Press Me </button>
function bgChange() {
var newColor……
document.body.style.backgroundColor = bgChange;
}

addEventListener() / removeEventListener: functions similar way to the event handler properties but the syntax is different.
var btn = document.querySelector("button");
function bgChange() {
// some code
}
btn.addEventListener("click", bgChange);


Event Handler vs add/removeEventListener: Event handler properties have less power and options, but better cross browser compatibility. While add/removeEventListener are more powerful, but can also become more complex and are less supported by browsers. The main advantage to using add/removeEventListener is that you can add multiple listeners to the same type of element if required. You can also call these on an element multiple times with different functions specified in the second argument(they scale better) This would be impossible with event handler properties because any subsequent attempts to set a property will overwrite the earlier ones.
element.addEventListener(<event-name>, <callback>, <use-capture>);
event-name (string) This is the name or type of event that you would like to listen to. It could be any of the standard DOM events (click, mousedown, touchstart, transitionEnd, etc.) or even your own custom event name (we’ll touch on custom events later).
callback (function) This function gets called when the event happens. The event object, containing data about the event, is passed as the first argument.
* use-capture (boolean) This declares whether the callback should be fired in the “capture” phase.

Event Objects: inside of event handler functions you might see a parameter specified with a name such as event, eve, or e. This is called an event object and is automatically passed to the event handler to provide extra features and information.

function bgChange(e) {
    var newColor
     // some code
     console.log(e);
}
btn.addEventListener("click", bgChange);


Event Delegation & Bubbling: Bubbling allows us to take advantage of event delegation. This concept relies on the fact that id you want code to run when you clock any one of a large number of child elements, you can set the event listener on their parent and have the effect of the event listener bubble to each child, rather than having to set the event listener on every child individually. A good example is a series of listed items - if you want each one to "pop up" with a message when clicked, you can set the click event listener on the the parent ur and it will bubble to the list items.
Event Delegation: You can trigger an event on a parent by clicking on a child element for example.
Event Bubbling Visual Demo: https://codepen.io/BertoOrt/pen/GmmarX
<ul> - adding the click event listener to the ul will "bubble" down and apply to all the li's.
     <li> test </li>
 <li> test </li>
</ul>


The term **elements** & **node elements** are used interchangeably but when people say the DOM is working with an element it is actually working with a node that __represents__ that element.


### Caching DOM Queries
Methods that find elements in the DOM tree are called **DOM queries**.

Note: When you need to work with an element more than once, you should use a variable to store the result of this query. This saves the browser looking through the DOM tree to find the same element(s) again. It is known as **caching** the selection. Programmers would say that the variable stores a "reference" to the object in the DOM tree (it is storing the location of the node.)

When people talk about storing elements in variables, they are really storing the location of the element(s) within the DOM tree in a variable. The properties and methods of that element node work on the variable.


### Selecting an individual element node

> getElementById()
Selects an individual element given the value of its id attribute.
Note: this is always quickest and most efficient way to access an element since ID's can be repeated.

> querySelector()
Uses CSS selector syntax that would select one or more elements. This method returns only the **first** of the matching elements.


### Selecting multiple elements (known as a NodeList)

> getElementsByClassName()
Selects one or more elements given the value of their class attribute.
Note: this method is faster than querySelectorAll().

> getElementsByTagName()
Selects ALL elements on the page with a specified tag name.
Note: this method is faster than querySelectorAll().

> querySelectorAll()
Uses CSS Selector syntax to select one or more elements and returns all of those matches.

### Traversing between element nodes

parentNode

previousSibling

nextSibling

firstChild

lastChild


**NodeLists** When a DOM method **can** return more that one element, it returns a NodeList (even if it only finds one matching element). A Nodelist is a collection of element nodes. Each node is given an index number ( a number that starts at 0, just like arrays)

Note: Nodelists look like arrays and are numbered like arrays, but they are not actually arrays, they are a type of object called a **collection**.


### Live and Static NodeLists

There are times when you will want to work with the same selection of elements several times, so the NodeList can be stored in a variable and re-used  (rather than collecting the same elements again).

**Live NodeList**
When a script updates the page, the NodeList is updated at the same time. All methods starting with **getElementsBy** return a live NodeLists. Note: they are faster to generate than static NodeLists.

**Static NodeList**
When a script updates the page the node list is NOTE updated. **querySelectors** return static NodeLists. They reflect the document WHEN the query was made. If the script changes the content on the page the NodeList is NOT updated to reflect those changes.

###### Breaking down all four parts of the DOM selection method below:

```
document.getElementById('one')
```

**document** --> Refers to the document object. You always have to access individual elements via the document object.

**. (member operator)** --> The dot notation indicates that the method (on the right) is being applied to the node on the left side of the period.

**method** --> The getElementById() method indicates that you want to find the element based upon the value of its ID attribute.

**parameter** --> The method needs to know the value of the id attribute on the element you want. It is the parameter of the method.


### the item() Method

There are two ways to select an element form a NodeList:

1. the item() method
> var firstItem = elements.item(0);

2. array syntax
> var firstItem = elements[0];

Note: Array syntax is preferred over the item() method because it is faster. Before selecting a node form a NodeList, check that is contains nodes. If you repeatedly use the NodeList, store it in a variable.

### Steps for DOM selecting/updating

1. Find the element nodes
```
var elements = document.getElementsByClassName("soccer"); // finds "soccer" elements
```

2. conditional (optional)
```
if (elements.length > 2) { // if 3 or more are found
}
```

3. Select (inside if statement in this example )
```
var el = elements[2] // selects the third element in the NodeList
```

4. Update/change value (inside if statement in this example)
```
el.className = "basketball";
```


##### Update this section of the DOM notes next.

**The Document Object Model - DOM**
The only purpose of the html is for the browser to ingest it  and turn it into the DOM, if you want to some nothing with it after then you can manipulate it via the DOM API. HTML is parsed into a DOM " a string to a tree" that string is rendered to the DOM so it displays a certain way. Every web browser has something called the DOM, where DOM is an acronym for Document Object Model. The DOM is an API, where API is an acronym for Application Programming Interface. Simply put, an API is a way for programs to interact with each-other.

> Write JavaScript against the DOM API
    * Includes event handlers for clicks, key events, submit events
    * Creates and appends DOM elements
    * Uses event delegation to capture events from dynamically added elements
    * Finds existing elements by id and className in order to make changes
    * Mutates properties on existing DOM elements such as style, classNames

> Target, create, and manipulate DOM Elements
    * Creates and appends DOM elements
    * Finds existing elements by id and className in order to make changes
    * Mutates properties on existing DOM elements such as style, classNames

**DOM Elements | Node Tree**
How the DOM models the document:

The DOM models (represents) the document as an object.Objects are nice because programs can interact with them easily. It would be hard if we had to interact with the document by having our programs read the HTML or use computer vision to interact with the browser window. This isn't just any object, it is a special data structure known as a tree. The data structure gets its name because it can be visually represented to look like a real world tree: a tree has a trunk, the trunk has branches, each branch can have more branches. The data structure tree has a root node (trunk), the root node has nodes (branches), a node (branch) can have other nodes (branches). The file system is a tree. The root directory / is the root node (trunk). It contains several other directories, each of these is a node (branch). Each of those directories contain other directories (nodes).


Just like a directory:
* A node contained in another node is known as the child node.
* A node that contains another node is known as the parent node.

How the HTML maps to the tree:
1. The <html></html> tag becomes the root node.
2. It has 2 child nodes: <head></head>, <body></body
3. The <head></head> node has a child node: <title></title>.
4. The <body></body> node has 2 child nodes: <h1></h1>, <div></div>.
5. The <div></div> node has a child node: <p></p>.


**Selection/Traversal**

querySelector(“ “) - only returns the first match.
querySelectorAll(“ “) - returns the selected “nodelist”

firstChild & lastChild - example: selecting the first and/or last node. (li’s inside a ul)
parentNode & childNode - example: selecting the ul would be the parentNode of an li (which would be considered the childNode)
previousSibling & nextSibling - adjacent node elements on the same level, example li’s that are next to each other.
nodeValue is a little more confusing to use, but faster than innerHTML
innerHTML parses content as HTML and takes longer.
textContent uses straight text, does not parse HTML, and is faster.
innerText Takes styles into consideration. It won't get hidden text for instance.
createElement -
createTextNode -
removeChild -
appendChild -
.setAttribute -
type this is the name of the event
target (node) - this is the dom node where the event originated.
preventDefault - (function) This prevents any default behavior from occurring that the user agent (i.e. browser) might carry out in relation to the event (for example, preventing a click event on an <a> element from loading a new page).
load event:  fires on any resource that has finished loading (including any dependent resources). This could be an image, stylesheet, script, video, audio file, document or window.

Form Validation
New.js ← example form file

function getFormData() {
This selects all form inputs by queryselector
 var data = new FormData(document.querySelector("#submittedForm"));
This collects all the form data
function getFormData() {
This selects all form inputs by queryselector
 var data = new FormData(document.querySelector("#submittedForm"));

Returns the data from the form itself? For this return the "name:" is the data that it is getting and "nameInput" is the "name" that is on the actual form field itself.
 return {
       name: data.get("nameInput"),
       city: data.get("cityInput"),
       state: data.get("stateInput"),
       country: data.get("countryInput"),
       division: data.get("divisionInput"),
 };
}
   .then(response => response.json())
   .then(response => {
     // log
     console.log(response);
   }).catch(console.error);
}


Events
Events: actions or occurrences that happen in the system you are programming, which the system tells you amour so you can respond to them in some way if desired. For example if the user clicks a button on a webpage you mights what to respond to that action by displaying info.
Click Event: common DOM event fired by the browser when you click on something with your mouse.
Event Handler: the "onclick" handler property is equal to an anonymous function which contains the code we want the click event to run.
document.querySelector ("html").onclick - function () {};
(is equivalent to)
var myHTML = document.querySelector("html");
myHTML.onclick = function() {};


Inline event handlers (do NOT use)
<button onclick="bgChange()"> Press Me </button>
function bgChange() {
var newColor……
document.body.style.backgroundColor = bgChange;
}

addEventListener() / removeEventListener: functions similar way to the event handler properties but the syntax is different.
var btn = document.querySelector("button");
function bgChange() {
// some code
}
btn.addEventListener("click", bgChange);


Event Handler vs add/removeEventListener: Event handler properties have less power and options, but better cross browser compatibility. While add/removeEventListener are more powerful, but can also become more complex and are less supported by browsers. The main advantage to using add/removeEventListener is that you can add multiple listeners to the same type of element if required. You can also call these on an element multiple times with different functions specified in the second argument(they scale better) This would be impossible with event handler properties because any subsequent attempts to set a property will overwrite the earlier ones.
element.addEventListener(<event-name>, <callback>, <use-capture>);
event-name (string) This is the name or type of event that you would like to listen to. It could be any of the standard DOM events (click, mousedown, touchstart, transitionEnd, etc.) or even your own custom event name (we’ll touch on custom events later).
callback (function) This function gets called when the event happens. The event object, containing data about the event, is passed as the first argument.
* use-capture (boolean) This declares whether the callback should be fired in the “capture” phase.

Event Objects: inside of event handler functions you might see a parameter specified with a name such as event, eve, or e. This is called an event object and is automatically passed to the event handler to provide extra features and information.

function bgChange(e) {
    var newColor
     // some code
     console.log(e);
}
btn.addEventListener("click", bgChange);


Event Delegation & Bubbling: Bubbling allows us to take advantage of event delegation. This concept relies on the fact that id you want code to run when you clock any one of a large number of child elements, you can set the event listener on their parent and have the effect of the event listener bubble to each child, rather than having to set the event listener on every child individually. A good example is a series of listed items - if you want each one to "pop up" with a message when clicked, you can set the click event listener on the the parent ur and it will bubble to the list items.
Event Delegation: You can trigger an event on a parent by clicking on a child element for example.
Event Bubbling Visual Demo: https://codepen.io/BertoOrt/pen/GmmarX
<ul> - adding the click event listener to the ul will "bubble" down and apply to all the li's.
     <li> test </li>
 <li> test </li>
</ul>


The term **elements** & **node elements** are used interchangeably but when people say the DOM is working with an element it is actually working with a node that __represents__ that element.


### Caching DOM Queries
Methods that find elements in the DOM tree are called **DOM queries**.

Note: When you need to work with an element more than once, you should use a variable to store the result of this query. This saves the browser looking through the DOM tree to find the same element(s) again. It is known as **caching** the selection. Programmers would say that the variable stores a "reference" to the object in the DOM tree (it is storing the location of the node.)

When people talk about storing elements in variables, they are really storing the location of the element(s) within the DOM tree in a variable. The properties and methods of that element node work on the variable.


### Selecting an individual element node

> getElementById()
Selects an individual element given the value of its id attribute.
Note: this is always quickest and most efficient way to access an element since ID's can be repeated.

> querySelector()
Uses CSS selector syntax that would select one or more elements. This method returns only the **first** of the matching elements.


### Selecting multiple elements (known as a NodeList)

> getElementsByClassName()
Selects one or more elements given the value of their class attribute.
Note: this method is faster than querySelectorAll().

> getElementsByTagName()
Selects ALL elements on the page with a specified tag name.
Note: this method is faster than querySelectorAll().

> querySelectorAll()
Uses CSS Selector syntax to select one or more elements and returns all of those matches.

### Traversing between element nodes

parentNode

previousSibling

nextSibling

firstChild

lastChild


**NodeLists** When a DOM method **can** return more that one element, it returns a NodeList (even if it only finds one matching element). A Nodelist is a collection of element nodes. Each node is given an index number ( a number that starts at 0, just like arrays)

Note: Nodelists look like arrays and are numbered like arrays, but they are not actually arrays, they are a type of object called a **collection**.


### Live and Static NodeLists

There are times when you will want to work with the same selection of elements several times, so the NodeList can be stored in a variable and re-used  (rather than collecting the same elements again).

**Live NodeList**
When a script updates the page, the NodeList is updated at the same time. All methods starting with **getElementsBy** return a live NodeLists. Note: they are faster to generate than static NodeLists.

**Static NodeList**
When a script updates the page the node list is NOTE updated. **querySelectors** return static NodeLists. They reflect the document WHEN the query was made. If the script changes the content on the page the NodeList is NOT updated to reflect those changes.

###### Breaking down all four parts of the DOM selection method below:

```
document.getElementById('one')
```

**document** --> Refers to the document object. You always have to access individual elements via the document object.

**. (member operator)** --> The dot notation indicates that the method (on the right) is being applied to the node on the left side of the period.

**method** --> The getElementById() method indicates that you want to find the element based upon the value of its ID attribute.

**parameter** --> The method needs to know the value of the id attribute on the element you want. It is the parameter of the method.


### the item() Method

There are two ways to select an element form a NodeList:

1. the item() method
> var firstItem = elements.item(0);

2. array syntax
> var firstItem = elements[0];

Note: Array syntax is preferred over the item() method because it is faster. Before selecting a node form a NodeList, check that is contains nodes. If you repeatedly use the NodeList, store it in a variable.

### Steps for DOM selecting/updating

1. Find the element nodes
```
var elements = document.getElementsByClassName("soccer"); // finds "soccer" elements
```

2. conditional (optional)
```
if (elements.length > 2) { // if 3 or more are found
}
```

3. Select (inside if statement in this example )
```
var el = elements[2] // selects the third element in the NodeList
```

4. Update/change value (inside if statement in this example)
```
el.className = "basketball";
```


##### Update this section of the DOM notes next.

**The Document Object Model - DOM**
The only purpose of the html is for the browser to ingest it  and turn it into the DOM, if you want to some nothing with it after then you can manipulate it via the DOM API. HTML is parsed into a DOM " a string to a tree" that string is rendered to the DOM so it displays a certain way. Every web browser has something called the DOM, where DOM is an acronym for Document Object Model. The DOM is an API, where API is an acronym for Application Programming Interface. Simply put, an API is a way for programs to interact with each-other.

> Write JavaScript against the DOM API
    * Includes event handlers for clicks, key events, submit events
    * Creates and appends DOM elements
    * Uses event delegation to capture events from dynamically added elements
    * Finds existing elements by id and className in order to make changes
    * Mutates properties on existing DOM elements such as style, classNames

> Target, create, and manipulate DOM Elements
    * Creates and appends DOM elements
    * Finds existing elements by id and className in order to make changes
    * Mutates properties on existing DOM elements such as style, classNames

**DOM Elements | Node Tree**
How the DOM models the document:

The DOM models (represents) the document as an object.Objects are nice because programs can interact with them easily. It would be hard if we had to interact with the document by having our programs read the HTML or use computer vision to interact with the browser window. This isn't just any object, it is a special data structure known as a tree. The data structure gets its name because it can be visually represented to look like a real world tree: a tree has a trunk, the trunk has branches, each branch can have more branches. The data structure tree has a root node (trunk), the root node has nodes (branches), a node (branch) can have other nodes (branches). The file system is a tree. The root directory / is the root node (trunk). It contains several other directories, each of these is a node (branch). Each of those directories contain other directories (nodes).


Just like a directory:
* A node contained in another node is known as the child node.
* A node that contains another node is known as the parent node.

How the HTML maps to the tree:
1. The <html></html> tag becomes the root node.
2. It has 2 child nodes: <head></head>, <body></body
3. The <head></head> node has a child node: <title></title>.
4. The <body></body> node has 2 child nodes: <h1></h1>, <div></div>.
5. The <div></div> node has a child node: <p></p>.


**Selection/Traversal**

querySelector(“ “) - only returns the first match.
querySelectorAll(“ “) - returns the selected “nodelist”

firstChild & lastChild - example: selecting the first and/or last node. (li’s inside a ul)
parentNode & childNode - example: selecting the ul would be the parentNode of an li (which would be considered the childNode)
previousSibling & nextSibling - adjacent node elements on the same level, example li’s that are next to each other.
nodeValue is a little more confusing to use, but faster than innerHTML
innerHTML parses content as HTML and takes longer.
textContent uses straight text, does not parse HTML, and is faster.
innerText Takes styles into consideration. It won't get hidden text for instance.
createElement -
createTextNode -
removeChild -
appendChild -
.setAttribute -
type this is the name of the event
target (node) - this is the dom node where the event originated.
preventDefault - (function) This prevents any default behavior from occurring that the user agent (i.e. browser) might carry out in relation to the event (for example, preventing a click event on an <a> element from loading a new page).
load event:  fires on any resource that has finished loading (including any dependent resources). This could be an image, stylesheet, script, video, audio file, document or window.

Form Validation
New.js ← example form file

function getFormData() {
This selects all form inputs by queryselector
 var data = new FormData(document.querySelector("#submittedForm"));
This collects all the form data
function getFormData() {
This selects all form inputs by queryselector
 var data = new FormData(document.querySelector("#submittedForm"));

Returns the data from the form itself? For this return the "name:" is the data that it is getting and "nameInput" is the "name" that is on the actual form field itself.
 return {
       name: data.get("nameInput"),
       city: data.get("cityInput"),
       state: data.get("stateInput"),
       country: data.get("countryInput"),
       division: data.get("divisionInput"),
 };
}
   .then(response => response.json())
   .then(response => {
     // log
     console.log(response);
   }).catch(console.error);
}


Events
Events: actions or occurrences that happen in the system you are programming, which the system tells you amour so you can respond to them in some way if desired. For example if the user clicks a button on a webpage you mights what to respond to that action by displaying info.
Click Event: common DOM event fired by the browser when you click on something with your mouse.
Event Handler: the "onclick" handler property is equal to an anonymous function which contains the code we want the click event to run.
document.querySelector ("html").onclick - function () {};
(is equivalent to)
var myHTML = document.querySelector("html");
myHTML.onclick = function() {};


Inline event handlers (do NOT use)
<button onclick="bgChange()"> Press Me </button>
function bgChange() {
var newColor……
document.body.style.backgroundColor = bgChange;
}

addEventListener() / removeEventListener: functions similar way to the event handler properties but the syntax is different.
var btn = document.querySelector("button");
function bgChange() {
// some code
}
btn.addEventListener("click", bgChange);


Event Handler vs add/removeEventListener: Event handler properties have less power and options, but better cross browser compatibility. While add/removeEventListener are more powerful, but can also become more complex and are less supported by browsers. The main advantage to using add/removeEventListener is that you can add multiple listeners to the same type of element if required. You can also call these on an element multiple times with different functions specified in the second argument(they scale better) This would be impossible with event handler properties because any subsequent attempts to set a property will overwrite the earlier ones.
element.addEventListener(<event-name>, <callback>, <use-capture>);
event-name (string) This is the name or type of event that you would like to listen to. It could be any of the standard DOM events (click, mousedown, touchstart, transitionEnd, etc.) or even your own custom event name (we’ll touch on custom events later).
callback (function) This function gets called when the event happens. The event object, containing data about the event, is passed as the first argument.
* use-capture (boolean) This declares whether the callback should be fired in the “capture” phase.

Event Objects: inside of event handler functions you might see a parameter specified with a name such as event, eve, or e. This is called an event object and is automatically passed to the event handler to provide extra features and information.

function bgChange(e) {
    var newColor
     // some code
     console.log(e);
}
btn.addEventListener("click", bgChange);


Event Delegation & Bubbling: Bubbling allows us to take advantage of event delegation. This concept relies on the fact that id you want code to run when you clock any one of a large number of child elements, you can set the event listener on their parent and have the effect of the event listener bubble to each child, rather than having to set the event listener on every child individually. A good example is a series of listed items - if you want each one to "pop up" with a message when clicked, you can set the click event listener on the the parent ur and it will bubble to the list items.
Event Delegation: You can trigger an event on a parent by clicking on a child element for example.
Event Bubbling Visual Demo: https://codepen.io/BertoOrt/pen/GmmarX
<ul> - adding the click event listener to the ul will "bubble" down and apply to all the li's.
     <li> test </li>
 <li> test </li>
</ul>


The term **elements** & **node elements** are used interchangeably but when people say the DOM is working with an element it is actually working with a node that __represents__ that element.


### Caching DOM Queries
Methods that find elements in the DOM tree are called **DOM queries**.

Note: When you need to work with an element more than once, you should use a variable to store the result of this query. This saves the browser looking through the DOM tree to find the same element(s) again. It is known as **caching** the selection. Programmers would say that the variable stores a "reference" to the object in the DOM tree (it is storing the location of the node.)

When people talk about storing elements in variables, they are really storing the location of the element(s) within the DOM tree in a variable. The properties and methods of that element node work on the variable.


### Selecting an individual element node

> getElementById()
Selects an individual element given the value of its id attribute.
Note: this is always quickest and most efficient way to access an element since ID's can be repeated.

> querySelector()
Uses CSS selector syntax that would select one or more elements. This method returns only the **first** of the matching elements.


### Selecting multiple elements (known as a NodeList)

> getElementsByClassName()
Selects one or more elements given the value of their class attribute.
Note: this method is faster than querySelectorAll().

> getElementsByTagName()
Selects ALL elements on the page with a specified tag name.
Note: this method is faster than querySelectorAll().

> querySelectorAll()
Uses CSS Selector syntax to select one or more elements and returns all of those matches.

### Traversing between element nodes

parentNode

previousSibling

nextSibling

firstChild

lastChild


**NodeLists** When a DOM method **can** return more that one element, it returns a NodeList (even if it only finds one matching element). A Nodelist is a collection of element nodes. Each node is given an index number ( a number that starts at 0, just like arrays)

Note: Nodelists look like arrays and are numbered like arrays, but they are not actually arrays, they are a type of object called a **collection**.


### Live and Static NodeLists

There are times when you will want to work with the same selection of elements several times, so the NodeList can be stored in a variable and re-used  (rather than collecting the same elements again).

**Live NodeList**
When a script updates the page, the NodeList is updated at the same time. All methods starting with **getElementsBy** return a live NodeLists. Note: they are faster to generate than static NodeLists.

**Static NodeList**
When a script updates the page the node list is NOTE updated. **querySelectors** return static NodeLists. They reflect the document WHEN the query was made. If the script changes the content on the page the NodeList is NOT updated to reflect those changes.

###### Breaking down all four parts of the DOM selection method below:

```
document.getElementById('one')
```

**document** --> Refers to the document object. You always have to access individual elements via the document object.

**. (member operator)** --> The dot notation indicates that the method (on the right) is being applied to the node on the left side of the period.

**method** --> The getElementById() method indicates that you want to find the element based upon the value of its ID attribute.

**parameter** --> The method needs to know the value of the id attribute on the element you want. It is the parameter of the method.


### the item() Method

There are two ways to select an element form a NodeList:

1. the item() method
> var firstItem = elements.item(0);

2. array syntax
> var firstItem = elements[0];

Note: Array syntax is preferred over the item() method because it is faster. Before selecting a node form a NodeList, check that is contains nodes. If you repeatedly use the NodeList, store it in a variable.

### Steps for DOM selecting/updating

1. Find the element nodes
```
var elements = document.getElementsByClassName("soccer"); // finds "soccer" elements
```

2. conditional (optional)
```
if (elements.length > 2) { // if 3 or more are found
}
```

3. Select (inside if statement in this example )
```
var el = elements[2] // selects the third element in the NodeList
```

4. Update/change value (inside if statement in this example)
```
el.className = "basketball";
```


##### Update this section of the DOM notes next.

**The Document Object Model - DOM**
The only purpose of the html is for the browser to ingest it  and turn it into the DOM, if you want to some nothing with it after then you can manipulate it via the DOM API. HTML is parsed into a DOM " a string to a tree" that string is rendered to the DOM so it displays a certain way. Every web browser has something called the DOM, where DOM is an acronym for Document Object Model. The DOM is an API, where API is an acronym for Application Programming Interface. Simply put, an API is a way for programs to interact with each-other.

> Write JavaScript against the DOM API
    * Includes event handlers for clicks, key events, submit events
    * Creates and appends DOM elements
    * Uses event delegation to capture events from dynamically added elements
    * Finds existing elements by id and className in order to make changes
    * Mutates properties on existing DOM elements such as style, classNames

> Target, create, and manipulate DOM Elements
    * Creates and appends DOM elements
    * Finds existing elements by id and className in order to make changes
    * Mutates properties on existing DOM elements such as style, classNames

**DOM Elements | Node Tree**
How the DOM models the document:

The DOM models (represents) the document as an object.Objects are nice because programs can interact with them easily. It would be hard if we had to interact with the document by having our programs read the HTML or use computer vision to interact with the browser window. This isn't just any object, it is a special data structure known as a tree. The data structure gets its name because it can be visually represented to look like a real world tree: a tree has a trunk, the trunk has branches, each branch can have more branches. The data structure tree has a root node (trunk), the root node has nodes (branches), a node (branch) can have other nodes (branches). The file system is a tree. The root directory / is the root node (trunk). It contains several other directories, each of these is a node (branch). Each of those directories contain other directories (nodes).


Just like a directory:
* A node contained in another node is known as the child node.
* A node that contains another node is known as the parent node.

How the HTML maps to the tree:
1. The <html></html> tag becomes the root node.
2. It has 2 child nodes: <head></head>, <body></body
3. The <head></head> node has a child node: <title></title>.
4. The <body></body> node has 2 child nodes: <h1></h1>, <div></div>.
5. The <div></div> node has a child node: <p></p>.


**Selection/Traversal**

querySelector(“ “) - only returns the first match.
querySelectorAll(“ “) - returns the selected “nodelist”

firstChild & lastChild - example: selecting the first and/or last node. (li’s inside a ul)
parentNode & childNode - example: selecting the ul would be the parentNode of an li (which would be considered the childNode)
previousSibling & nextSibling - adjacent node elements on the same level, example li’s that are next to each other.
nodeValue is a little more confusing to use, but faster than innerHTML
innerHTML parses content as HTML and takes longer.
textContent uses straight text, does not parse HTML, and is faster.
innerText Takes styles into consideration. It won't get hidden text for instance.
createElement -
createTextNode -
removeChild -
appendChild -
.setAttribute -
type this is the name of the event
target (node) - this is the dom node where the event originated.
preventDefault - (function) This prevents any default behavior from occurring that the user agent (i.e. browser) might carry out in relation to the event (for example, preventing a click event on an <a> element from loading a new page).
load event:  fires on any resource that has finished loading (including any dependent resources). This could be an image, stylesheet, script, video, audio file, document or window.

Form Validation
New.js ← example form file

function getFormData() {
This selects all form inputs by queryselector
 var data = new FormData(document.querySelector("#submittedForm"));
This collects all the form data
function getFormData() {
This selects all form inputs by queryselector
 var data = new FormData(document.querySelector("#submittedForm"));

Returns the data from the form itself? For this return the "name:" is the data that it is getting and "nameInput" is the "name" that is on the actual form field itself.
 return {
       name: data.get("nameInput"),
       city: data.get("cityInput"),
       state: data.get("stateInput"),
       country: data.get("countryInput"),
       division: data.get("divisionInput"),
 };
}
   .then(response => response.json())
   .then(response => {
     // log
     console.log(response);
   }).catch(console.error);
}


Events
Events: actions or occurrences that happen in the system you are programming, which the system tells you amour so you can respond to them in some way if desired. For example if the user clicks a button on a webpage you mights what to respond to that action by displaying info.
Click Event: common DOM event fired by the browser when you click on something with your mouse.
Event Handler: the "onclick" handler property is equal to an anonymous function which contains the code we want the click event to run.
document.querySelector ("html").onclick - function () {};
(is equivalent to)
var myHTML = document.querySelector("html");
myHTML.onclick = function() {};


Inline event handlers (do NOT use)
<button onclick="bgChange()"> Press Me </button>
function bgChange() {
var newColor……
document.body.style.backgroundColor = bgChange;
}

addEventListener() / removeEventListener: functions similar way to the event handler properties but the syntax is different.
var btn = document.querySelector("button");
function bgChange() {
// some code
}
btn.addEventListener("click", bgChange);


Event Handler vs add/removeEventListener: Event handler properties have less power and options, but better cross browser compatibility. While add/removeEventListener are more powerful, but can also become more complex and are less supported by browsers. The main advantage to using add/removeEventListener is that you can add multiple listeners to the same type of element if required. You can also call these on an element multiple times with different functions specified in the second argument(they scale better) This would be impossible with event handler properties because any subsequent attempts to set a property will overwrite the earlier ones.
element.addEventListener(<event-name>, <callback>, <use-capture>);
event-name (string) This is the name or type of event that you would like to listen to. It could be any of the standard DOM events (click, mousedown, touchstart, transitionEnd, etc.) or even your own custom event name (we’ll touch on custom events later).
callback (function) This function gets called when the event happens. The event object, containing data about the event, is passed as the first argument.
* use-capture (boolean) This declares whether the callback should be fired in the “capture” phase.

Event Objects: inside of event handler functions you might see a parameter specified with a name such as event, eve, or e. This is called an event object and is automatically passed to the event handler to provide extra features and information.

function bgChange(e) {
    var newColor
     // some code
     console.log(e);
}
btn.addEventListener("click", bgChange);


Event Delegation & Bubbling: Bubbling allows us to take advantage of event delegation. This concept relies on the fact that id you want code to run when you clock any one of a large number of child elements, you can set the event listener on their parent and have the effect of the event listener bubble to each child, rather than having to set the event listener on every child individually. A good example is a series of listed items - if you want each one to "pop up" with a message when clicked, you can set the click event listener on the the parent ur and it will bubble to the list items.
Event Delegation: You can trigger an event on a parent by clicking on a child element for example.
Event Bubbling Visual Demo: https://codepen.io/BertoOrt/pen/GmmarX
<ul> - adding the click event listener to the ul will "bubble" down and apply to all the li's.
     <li> test </li>
 <li> test </li>
</ul>


The term **elements** & **node elements** are used interchangeably but when people say the DOM is working with an element it is actually working with a node that __represents__ that element.


### Caching DOM Queries
Methods that find elements in the DOM tree are called **DOM queries**.

Note: When you need to work with an element more than once, you should use a variable to store the result of this query. This saves the browser looking through the DOM tree to find the same element(s) again. It is known as **caching** the selection. Programmers would say that the variable stores a "reference" to the object in the DOM tree (it is storing the location of the node.)

When people talk about storing elements in variables, they are really storing the location of the element(s) within the DOM tree in a variable. The properties and methods of that element node work on the variable.


### Selecting an individual element node

> getElementById()
Selects an individual element given the value of its id attribute.
Note: this is always quickest and most efficient way to access an element since ID's can be repeated.

> querySelector()
Uses CSS selector syntax that would select one or more elements. This method returns only the **first** of the matching elements.


### Selecting multiple elements (known as a NodeList)

> getElementsByClassName()
Selects one or more elements given the value of their class attribute.
Note: this method is faster than querySelectorAll().

> getElementsByTagName()
Selects ALL elements on the page with a specified tag name.
Note: this method is faster than querySelectorAll().

> querySelectorAll()
Uses CSS Selector syntax to select one or more elements and returns all of those matches.

### Traversing between element nodes

parentNode

previousSibling

nextSibling

firstChild

lastChild


**NodeLists** When a DOM method **can** return more that one element, it returns a NodeList (even if it only finds one matching element). A Nodelist is a collection of element nodes. Each node is given an index number ( a number that starts at 0, just like arrays)

Note: Nodelists look like arrays and are numbered like arrays, but they are not actually arrays, they are a type of object called a **collection**.


### Live and Static NodeLists

There are times when you will want to work with the same selection of elements several times, so the NodeList can be stored in a variable and re-used  (rather than collecting the same elements again).

**Live NodeList**
When a script updates the page, the NodeList is updated at the same time. All methods starting with **getElementsBy** return a live NodeLists. Note: they are faster to generate than static NodeLists.

**Static NodeList**
When a script updates the page the node list is NOTE updated. **querySelectors** return static NodeLists. They reflect the document WHEN the query was made. If the script changes the content on the page the NodeList is NOT updated to reflect those changes.

###### Breaking down all four parts of the DOM selection method below:

```
document.getElementById('one')
```

**document** --> Refers to the document object. You always have to access individual elements via the document object.

**. (member operator)** --> The dot notation indicates that the method (on the right) is being applied to the node on the left side of the period.

**method** --> The getElementById() method indicates that you want to find the element based upon the value of its ID attribute.

**parameter** --> The method needs to know the value of the id attribute on the element you want. It is the parameter of the method.


### the item() Method

There are two ways to select an element form a NodeList:

1. the item() method
> var firstItem = elements.item(0);

2. array syntax
> var firstItem = elements[0];

Note: Array syntax is preferred over the item() method because it is faster. Before selecting a node form a NodeList, check that is contains nodes. If you repeatedly use the NodeList, store it in a variable.

### Steps for DOM selecting/updating

1. Find the element nodes
```
var elements = document.getElementsByClassName("soccer"); // finds "soccer" elements
```

2. conditional (optional)
```
if (elements.length > 2) { // if 3 or more are found
}
```

3. Select (inside if statement in this example )
```
var el = elements[2] // selects the third element in the NodeList
```

4. Update/change value (inside if statement in this example)
```
el.className = "basketball";
```


##### Update this section of the DOM notes next.

**The Document Object Model - DOM**
The only purpose of the html is for the browser to ingest it  and turn it into the DOM, if you want to some nothing with it after then you can manipulate it via the DOM API. HTML is parsed into a DOM " a string to a tree" that string is rendered to the DOM so it displays a certain way. Every web browser has something called the DOM, where DOM is an acronym for Document Object Model. The DOM is an API, where API is an acronym for Application Programming Interface. Simply put, an API is a way for programs to interact with each-other.

> Write JavaScript against the DOM API
    * Includes event handlers for clicks, key events, submit events
    * Creates and appends DOM elements
    * Uses event delegation to capture events from dynamically added elements
    * Finds existing elements by id and className in order to make changes
    * Mutates properties on existing DOM elements such as style, classNames

> Target, create, and manipulate DOM Elements
    * Creates and appends DOM elements
    * Finds existing elements by id and className in order to make changes
    * Mutates properties on existing DOM elements such as style, classNames

**DOM Elements | Node Tree**
How the DOM models the document:

The DOM models (represents) the document as an object.Objects are nice because programs can interact with them easily. It would be hard if we had to interact with the document by having our programs read the HTML or use computer vision to interact with the browser window. This isn't just any object, it is a special data structure known as a tree. The data structure gets its name because it can be visually represented to look like a real world tree: a tree has a trunk, the trunk has branches, each branch can have more branches. The data structure tree has a root node (trunk), the root node has nodes (branches), a node (branch) can have other nodes (branches). The file system is a tree. The root directory / is the root node (trunk). It contains several other directories, each of these is a node (branch). Each of those directories contain other directories (nodes).


Just like a directory:
* A node contained in another node is known as the child node.
* A node that contains another node is known as the parent node.

How the HTML maps to the tree:
1. The <html></html> tag becomes the root node.
2. It has 2 child nodes: <head></head>, <body></body
3. The <head></head> node has a child node: <title></title>.
4. The <body></body> node has 2 child nodes: <h1></h1>, <div></div>.
5. The <div></div> node has a child node: <p></p>.


**Selection/Traversal**

querySelector(“ “) - only returns the first match.
querySelectorAll(“ “) - returns the selected “nodelist”

firstChild & lastChild - example: selecting the first and/or last node. (li’s inside a ul)
parentNode & childNode - example: selecting the ul would be the parentNode of an li (which would be considered the childNode)
previousSibling & nextSibling - adjacent node elements on the same level, example li’s that are next to each other.
nodeValue is a little more confusing to use, but faster than innerHTML
innerHTML parses content as HTML and takes longer.
textContent uses straight text, does not parse HTML, and is faster.
innerText Takes styles into consideration. It won't get hidden text for instance.
createElement -
createTextNode -
removeChild -
appendChild -
.setAttribute -
type this is the name of the event
target (node) - this is the dom node where the event originated.
preventDefault - (function) This prevents any default behavior from occurring that the user agent (i.e. browser) might carry out in relation to the event (for example, preventing a click event on an <a> element from loading a new page).
load event:  fires on any resource that has finished loading (including any dependent resources). This could be an image, stylesheet, script, video, audio file, document or window.

Form Validation
New.js ← example form file

function getFormData() {
This selects all form inputs by queryselector
 var data = new FormData(document.querySelector("#submittedForm"));
This collects all the form data
function getFormData() {
This selects all form inputs by queryselector
 var data = new FormData(document.querySelector("#submittedForm"));

Returns the data from the form itself? For this return the "name:" is the data that it is getting and "nameInput" is the "name" that is on the actual form field itself.
 return {
       name: data.get("nameInput"),
       city: data.get("cityInput"),
       state: data.get("stateInput"),
       country: data.get("countryInput"),
       division: data.get("divisionInput"),
 };
}
   .then(response => response.json())
   .then(response => {
     // log
     console.log(response);
   }).catch(console.error);
}


Events
Events: actions or occurrences that happen in the system you are programming, which the system tells you amour so you can respond to them in some way if desired. For example if the user clicks a button on a webpage you mights what to respond to that action by displaying info.
Click Event: common DOM event fired by the browser when you click on something with your mouse.
Event Handler: the "onclick" handler property is equal to an anonymous function which contains the code we want the click event to run.
document.querySelector ("html").onclick - function () {};
(is equivalent to)
var myHTML = document.querySelector("html");
myHTML.onclick = function() {};


Inline event handlers (do NOT use)
<button onclick="bgChange()"> Press Me </button>
function bgChange() {
var newColor……
document.body.style.backgroundColor = bgChange;
}

addEventListener() / removeEventListener: functions similar way to the event handler properties but the syntax is different.
var btn = document.querySelector("button");
function bgChange() {
// some code
}
btn.addEventListener("click", bgChange);


Event Handler vs add/removeEventListener: Event handler properties have less power and options, but better cross browser compatibility. While add/removeEventListener are more powerful, but can also become more complex and are less supported by browsers. The main advantage to using add/removeEventListener is that you can add multiple listeners to the same type of element if required. You can also call these on an element multiple times with different functions specified in the second argument(they scale better) This would be impossible with event handler properties because any subsequent attempts to set a property will overwrite the earlier ones.
element.addEventListener(<event-name>, <callback>, <use-capture>);
event-name (string) This is the name or type of event that you would like to listen to. It could be any of the standard DOM events (click, mousedown, touchstart, transitionEnd, etc.) or even your own custom event name (we’ll touch on custom events later).
callback (function) This function gets called when the event happens. The event object, containing data about the event, is passed as the first argument.
* use-capture (boolean) This declares whether the callback should be fired in the “capture” phase.

Event Objects: inside of event handler functions you might see a parameter specified with a name such as event, eve, or e. This is called an event object and is automatically passed to the event handler to provide extra features and information.

function bgChange(e) {
    var newColor
     // some code
     console.log(e);
}
btn.addEventListener("click", bgChange);


Event Delegation & Bubbling: Bubbling allows us to take advantage of event delegation. This concept relies on the fact that id you want code to run when you clock any one of a large number of child elements, you can set the event listener on their parent and have the effect of the event listener bubble to each child, rather than having to set the event listener on every child individually. A good example is a series of listed items - if you want each one to "pop up" with a message when clicked, you can set the click event listener on the the parent ur and it will bubble to the list items.
Event Delegation: You can trigger an event on a parent by clicking on a child element for example.
Event Bubbling Visual Demo: https://codepen.io/BertoOrt/pen/GmmarX
<ul> - adding the click event listener to the ul will "bubble" down and apply to all the li's.
     <li> test </li>
 <li> test </li>
</ul>


The term **elements** & **node elements** are used interchangeably but when people say the DOM is working with an element it is actually working with a node that __represents__ that element.


### Caching DOM Queries
Methods that find elements in the DOM tree are called **DOM queries**.

Note: When you need to work with an element more than once, you should use a variable to store the result of this query. This saves the browser looking through the DOM tree to find the same element(s) again. It is known as **caching** the selection. Programmers would say that the variable stores a "reference" to the object in the DOM tree (it is storing the location of the node.)

When people talk about storing elements in variables, they are really storing the location of the element(s) within the DOM tree in a variable. The properties and methods of that element node work on the variable.


### Selecting an individual element node

> getElementById()
Selects an individual element given the value of its id attribute.
Note: this is always quickest and most efficient way to access an element since ID's can be repeated.

> querySelector()
Uses CSS selector syntax that would select one or more elements. This method returns only the **first** of the matching elements.


### Selecting multiple elements (known as a NodeList)

> getElementsByClassName()
Selects one or more elements given the value of their class attribute.
Note: this method is faster than querySelectorAll().

> getElementsByTagName()
Selects ALL elements on the page with a specified tag name.
Note: this method is faster than querySelectorAll().

> querySelectorAll()
Uses CSS Selector syntax to select one or more elements and returns all of those matches.

### Traversing between element nodes

parentNode

previousSibling

nextSibling

firstChild

lastChild


**NodeLists** When a DOM method **can** return more that one element, it returns a NodeList (even if it only finds one matching element). A Nodelist is a collection of element nodes. Each node is given an index number ( a number that starts at 0, just like arrays)

Note: Nodelists look like arrays and are numbered like arrays, but they are not actually arrays, they are a type of object called a **collection**.


### Live and Static NodeLists

There are times when you will want to work with the same selection of elements several times, so the NodeList can be stored in a variable and re-used  (rather than collecting the same elements again).

**Live NodeList**
When a script updates the page, the NodeList is updated at the same time. All methods starting with **getElementsBy** return a live NodeLists. Note: they are faster to generate than static NodeLists.

**Static NodeList**
When a script updates the page the node list is NOTE updated. **querySelectors** return static NodeLists. They reflect the document WHEN the query was made. If the script changes the content on the page the NodeList is NOT updated to reflect those changes.

###### Breaking down all four parts of the DOM selection method below:

```
document.getElementById('one')
```

**document** --> Refers to the document object. You always have to access individual elements via the document object.

**. (member operator)** --> The dot notation indicates that the method (on the right) is being applied to the node on the left side of the period.

**method** --> The getElementById() method indicates that you want to find the element based upon the value of its ID attribute.

**parameter** --> The method needs to know the value of the id attribute on the element you want. It is the parameter of the method.


### the item() Method

There are two ways to select an element form a NodeList:

1. the item() method
> var firstItem = elements.item(0);

2. array syntax
> var firstItem = elements[0];

Note: Array syntax is preferred over the item() method because it is faster. Before selecting a node form a NodeList, check that is contains nodes. If you repeatedly use the NodeList, store it in a variable.

### Steps for DOM selecting/updating

1. Find the element nodes
```
var elements = document.getElementsByClassName("soccer"); // finds "soccer" elements
```

2. conditional (optional)
```
if (elements.length > 2) { // if 3 or more are found
}
```

3. Select (inside if statement in this example )
```
var el = elements[2] // selects the third element in the NodeList
```

4. Update/change value (inside if statement in this example)
```
el.className = "basketball";
```


##### Update this section of the DOM notes next.

**The Document Object Model - DOM**
The only purpose of the html is for the browser to ingest it  and turn it into the DOM, if you want to some nothing with it after then you can manipulate it via the DOM API. HTML is parsed into a DOM " a string to a tree" that string is rendered to the DOM so it displays a certain way. Every web browser has something called the DOM, where DOM is an acronym for Document Object Model. The DOM is an API, where API is an acronym for Application Programming Interface. Simply put, an API is a way for programs to interact with each-other.

> Write JavaScript against the DOM API
    * Includes event handlers for clicks, key events, submit events
    * Creates and appends DOM elements
    * Uses event delegation to capture events from dynamically added elements
    * Finds existing elements by id and className in order to make changes
    * Mutates properties on existing DOM elements such as style, classNames

> Target, create, and manipulate DOM Elements
    * Creates and appends DOM elements
    * Finds existing elements by id and className in order to make changes
    * Mutates properties on existing DOM elements such as style, classNames

**DOM Elements | Node Tree**
How the DOM models the document:

The DOM models (represents) the document as an object.Objects are nice because programs can interact with them easily. It would be hard if we had to interact with the document by having our programs read the HTML or use computer vision to interact with the browser window. This isn't just any object, it is a special data structure known as a tree. The data structure gets its name because it can be visually represented to look like a real world tree: a tree has a trunk, the trunk has branches, each branch can have more branches. The data structure tree has a root node (trunk), the root node has nodes (branches), a node (branch) can have other nodes (branches). The file system is a tree. The root directory / is the root node (trunk). It contains several other directories, each of these is a node (branch). Each of those directories contain other directories (nodes).


Just like a directory:
* A node contained in another node is known as the child node.
* A node that contains another node is known as the parent node.

How the HTML maps to the tree:
1. The <html></html> tag becomes the root node.
2. It has 2 child nodes: <head></head>, <body></body
3. The <head></head> node has a child node: <title></title>.
4. The <body></body> node has 2 child nodes: <h1></h1>, <div></div>.
5. The <div></div> node has a child node: <p></p>.


**Selection/Traversal**

querySelector(“ “) - only returns the first match.
querySelectorAll(“ “) - returns the selected “nodelist”

firstChild & lastChild - example: selecting the first and/or last node. (li’s inside a ul)
parentNode & childNode - example: selecting the ul would be the parentNode of an li (which would be considered the childNode)
previousSibling & nextSibling - adjacent node elements on the same level, example li’s that are next to each other.
nodeValue is a little more confusing to use, but faster than innerHTML
innerHTML parses content as HTML and takes longer.
textContent uses straight text, does not parse HTML, and is faster.
innerText Takes styles into consideration. It won't get hidden text for instance.
createElement -
createTextNode -
removeChild -
appendChild -
.setAttribute -
type this is the name of the event
target (node) - this is the dom node where the event originated.
preventDefault - (function) This prevents any default behavior from occurring that the user agent (i.e. browser) might carry out in relation to the event (for example, preventing a click event on an <a> element from loading a new page).
load event:  fires on any resource that has finished loading (including any dependent resources). This could be an image, stylesheet, script, video, audio file, document or window.

Form Validation
New.js ← example form file

function getFormData() {
This selects all form inputs by queryselector
 var data = new FormData(document.querySelector("#submittedForm"));
This collects all the form data
function getFormData() {
This selects all form inputs by queryselector
 var data = new FormData(document.querySelector("#submittedForm"));

Returns the data from the form itself? For this return the "name:" is the data that it is getting and "nameInput" is the "name" that is on the actual form field itself.
 return {
       name: data.get("nameInput"),
       city: data.get("cityInput"),
       state: data.get("stateInput"),
       country: data.get("countryInput"),
       division: data.get("divisionInput"),
 };
}
   .then(response => response.json())
   .then(response => {
     // log
     console.log(response);
   }).catch(console.error);
}


Events
Events: actions or occurrences that happen in the system you are programming, which the system tells you amour so you can respond to them in some way if desired. For example if the user clicks a button on a webpage you mights what to respond to that action by displaying info.
Click Event: common DOM event fired by the browser when you click on something with your mouse.
Event Handler: the "onclick" handler property is equal to an anonymous function which contains the code we want the click event to run.
document.querySelector ("html").onclick - function () {};
(is equivalent to)
var myHTML = document.querySelector("html");
myHTML.onclick = function() {};


Inline event handlers (do NOT use)
<button onclick="bgChange()"> Press Me </button>
function bgChange() {
var newColor……
document.body.style.backgroundColor = bgChange;
}

addEventListener() / removeEventListener: functions similar way to the event handler properties but the syntax is different.
var btn = document.querySelector("button");
function bgChange() {
// some code
}
btn.addEventListener("click", bgChange);


Event Handler vs add/removeEventListener: Event handler properties have less power and options, but better cross browser compatibility. While add/removeEventListener are more powerful, but can also become more complex and are less supported by browsers. The main advantage to using add/removeEventListener is that you can add multiple listeners to the same type of element if required. You can also call these on an element multiple times with different functions specified in the second argument(they scale better) This would be impossible with event handler properties because any subsequent attempts to set a property will overwrite the earlier ones.
element.addEventListener(<event-name>, <callback>, <use-capture>);
event-name (string) This is the name or type of event that you would like to listen to. It could be any of the standard DOM events (click, mousedown, touchstart, transitionEnd, etc.) or even your own custom event name (we’ll touch on custom events later).
callback (function) This function gets called when the event happens. The event object, containing data about the event, is passed as the first argument.
* use-capture (boolean) This declares whether the callback should be fired in the “capture” phase.

Event Objects: inside of event handler functions you might see a parameter specified with a name such as event, eve, or e. This is called an event object and is automatically passed to the event handler to provide extra features and information.

function bgChange(e) {
    var newColor
     // some code
     console.log(e);
}
btn.addEventListener("click", bgChange);


Event Delegation & Bubbling: Bubbling allows us to take advantage of event delegation. This concept relies on the fact that id you want code to run when you clock any one of a large number of child elements, you can set the event listener on their parent and have the effect of the event listener bubble to each child, rather than having to set the event listener on every child individually. A good example is a series of listed items - if you want each one to "pop up" with a message when clicked, you can set the click event listener on the the parent ur and it will bubble to the list items.
Event Delegation: You can trigger an event on a parent by clicking on a child element for example.
Event Bubbling Visual Demo: https://codepen.io/BertoOrt/pen/GmmarX
<ul> - adding the click event listener to the ul will "bubble" down and apply to all the li's.
     <li> test </li>
 <li> test </li>
</ul>


The term **elements** & **node elements** are used interchangeably but when people say the DOM is working with an element it is actually working with a node that __represents__ that element.


### Caching DOM Queries
Methods that find elements in the DOM tree are called **DOM queries**.

Note: When you need to work with an element more than once, you should use a variable to store the result of this query. This saves the browser looking through the DOM tree to find the same element(s) again. It is known as **caching** the selection. Programmers would say that the variable stores a "reference" to the object in the DOM tree (it is storing the location of the node.)

When people talk about storing elements in variables, they are really storing the location of the element(s) within the DOM tree in a variable. The properties and methods of that element node work on the variable.


### Selecting an individual element node

> getElementById()
Selects an individual element given the value of its id attribute.
Note: this is always quickest and most efficient way to access an element since ID's can be repeated.

> querySelector()
Uses CSS selector syntax that would select one or more elements. This method returns only the **first** of the matching elements.


### Selecting multiple elements (known as a NodeList)

> getElementsByClassName()
Selects one or more elements given the value of their class attribute.
Note: this method is faster than querySelectorAll().

> getElementsByTagName()
Selects ALL elements on the page with a specified tag name.
Note: this method is faster than querySelectorAll().

> querySelectorAll()
Uses CSS Selector syntax to select one or more elements and returns all of those matches.

### Traversing between element nodes

parentNode

previousSibling

nextSibling

firstChild

lastChild


**NodeLists** When a DOM method **can** return more that one element, it returns a NodeList (even if it only finds one matching element). A Nodelist is a collection of element nodes. Each node is given an index number ( a number that starts at 0, just like arrays)

Note: Nodelists look like arrays and are numbered like arrays, but they are not actually arrays, they are a type of object called a **collection**.


### Live and Static NodeLists

There are times when you will want to work with the same selection of elements several times, so the NodeList can be stored in a variable and re-used  (rather than collecting the same elements again).

**Live NodeList**
When a script updates the page, the NodeList is updated at the same time. All methods starting with **getElementsBy** return a live NodeLists. Note: they are faster to generate than static NodeLists.

**Static NodeList**
When a script updates the page the node list is NOTE updated. **querySelectors** return static NodeLists. They reflect the document WHEN the query was made. If the script changes the content on the page the NodeList is NOT updated to reflect those changes.

###### Breaking down all four parts of the DOM selection method below:

```
document.getElementById('one')
```

**document** --> Refers to the document object. You always have to access individual elements via the document object.

**. (member operator)** --> The dot notation indicates that the method (on the right) is being applied to the node on the left side of the period.

**method** --> The getElementById() method indicates that you want to find the element based upon the value of its ID attribute.

**parameter** --> The method needs to know the value of the id attribute on the element you want. It is the parameter of the method.


### the item() Method

There are two ways to select an element form a NodeList:

1. the item() method
> var firstItem = elements.item(0);

2. array syntax
> var firstItem = elements[0];

Note: Array syntax is preferred over the item() method because it is faster. Before selecting a node form a NodeList, check that is contains nodes. If you repeatedly use the NodeList, store it in a variable.

### Steps for DOM selecting/updating

1. Find the element nodes
```
var elements = document.getElementsByClassName("soccer"); // finds "soccer" elements
```

2. conditional (optional)
```
if (elements.length > 2) { // if 3 or more are found
}
```

3. Select (inside if statement in this example )
```
var el = elements[2] // selects the third element in the NodeList
```

4. Update/change value (inside if statement in this example)
```
el.className = "basketball";
```


##### Update this section of the DOM notes next.

**The Document Object Model - DOM**
The only purpose of the html is for the browser to ingest it  and turn it into the DOM, if you want to some nothing with it after then you can manipulate it via the DOM API. HTML is parsed into a DOM " a string to a tree" that string is rendered to the DOM so it displays a certain way. Every web browser has something called the DOM, where DOM is an acronym for Document Object Model. The DOM is an API, where API is an acronym for Application Programming Interface. Simply put, an API is a way for programs to interact with each-other.

> Write JavaScript against the DOM API
    * Includes event handlers for clicks, key events, submit events
    * Creates and appends DOM elements
    * Uses event delegation to capture events from dynamically added elements
    * Finds existing elements by id and className in order to make changes
    * Mutates properties on existing DOM elements such as style, classNames

> Target, create, and manipulate DOM Elements
    * Creates and appends DOM elements
    * Finds existing elements by id and className in order to make changes
    * Mutates properties on existing DOM elements such as style, classNames

**DOM Elements | Node Tree**
How the DOM models the document:

The DOM models (represents) the document as an object.Objects are nice because programs can interact with them easily. It would be hard if we had to interact with the document by having our programs read the HTML or use computer vision to interact with the browser window. This isn't just any object, it is a special data structure known as a tree. The data structure gets its name because it can be visually represented to look like a real world tree: a tree has a trunk, the trunk has branches, each branch can have more branches. The data structure tree has a root node (trunk), the root node has nodes (branches), a node (branch) can have other nodes (branches). The file system is a tree. The root directory / is the root node (trunk). It contains several other directories, each of these is a node (branch). Each of those directories contain other directories (nodes).


Just like a directory:
* A node contained in another node is known as the child node.
* A node that contains another node is known as the parent node.

How the HTML maps to the tree:
1. The <html></html> tag becomes the root node.
2. It has 2 child nodes: <head></head>, <body></body
3. The <head></head> node has a child node: <title></title>.
4. The <body></body> node has 2 child nodes: <h1></h1>, <div></div>.
5. The <div></div> node has a child node: <p></p>.


**Selection/Traversal**

querySelector(“ “) - only returns the first match.
querySelectorAll(“ “) - returns the selected “nodelist”

firstChild & lastChild - example: selecting the first and/or last node. (li’s inside a ul)
parentNode & childNode - example: selecting the ul would be the parentNode of an li (which would be considered the childNode)
previousSibling & nextSibling - adjacent node elements on the same level, example li’s that are next to each other.
nodeValue is a little more confusing to use, but faster than innerHTML
innerHTML parses content as HTML and takes longer.
textContent uses straight text, does not parse HTML, and is faster.
innerText Takes styles into consideration. It won't get hidden text for instance.
createElement -
createTextNode -
removeChild -
appendChild -
.setAttribute -
type this is the name of the event
target (node) - this is the dom node where the event originated.
preventDefault - (function) This prevents any default behavior from occurring that the user agent (i.e. browser) might carry out in relation to the event (for example, preventing a click event on an <a> element from loading a new page).
load event:  fires on any resource that has finished loading (including any dependent resources). This could be an image, stylesheet, script, video, audio file, document or window.

Form Validation
New.js ← example form file

function getFormData() {
This selects all form inputs by queryselector
 var data = new FormData(document.querySelector("#submittedForm"));
This collects all the form data
function getFormData() {
This selects all form inputs by queryselector
 var data = new FormData(document.querySelector("#submittedForm"));

Returns the data from the form itself? For this return the "name:" is the data that it is getting and "nameInput" is the "name" that is on the actual form field itself.
 return {
       name: data.get("nameInput"),
       city: data.get("cityInput"),
       state: data.get("stateInput"),
       country: data.get("countryInput"),
       division: data.get("divisionInput"),
 };
}
   .then(response => response.json())
   .then(response => {
     // log
     console.log(response);
   }).catch(console.error);
}


Events
Events: actions or occurrences that happen in the system you are programming, which the system tells you amour so you can respond to them in some way if desired. For example if the user clicks a button on a webpage you mights what to respond to that action by displaying info.
Click Event: common DOM event fired by the browser when you click on something with your mouse.
Event Handler: the "onclick" handler property is equal to an anonymous function which contains the code we want the click event to run.
document.querySelector ("html").onclick - function () {};
(is equivalent to)
var myHTML = document.querySelector("html");
myHTML.onclick = function() {};


Inline event handlers (do NOT use)
<button onclick="bgChange()"> Press Me </button>
function bgChange() {
var newColor……
document.body.style.backgroundColor = bgChange;
}

addEventListener() / removeEventListener: functions similar way to the event handler properties but the syntax is different.
var btn = document.querySelector("button");
function bgChange() {
// some code
}
btn.addEventListener("click", bgChange);


Event Handler vs add/removeEventListener: Event handler properties have less power and options, but better cross browser compatibility. While add/removeEventListener are more powerful, but can also become more complex and are less supported by browsers. The main advantage to using add/removeEventListener is that you can add multiple listeners to the same type of element if required. You can also call these on an element multiple times with different functions specified in the second argument(they scale better) This would be impossible with event handler properties because any subsequent attempts to set a property will overwrite the earlier ones.
element.addEventListener(<event-name>, <callback>, <use-capture>);
event-name (string) This is the name or type of event that you would like to listen to. It could be any of the standard DOM events (click, mousedown, touchstart, transitionEnd, etc.) or even your own custom event name (we’ll touch on custom events later).
callback (function) This function gets called when the event happens. The event object, containing data about the event, is passed as the first argument.
* use-capture (boolean) This declares whether the callback should be fired in the “capture” phase.

Event Objects: inside of event handler functions you might see a parameter specified with a name such as event, eve, or e. This is called an event object and is automatically passed to the event handler to provide extra features and information.

function bgChange(e) {
    var newColor
     // some code
     console.log(e);
The term **elements** & **node elements** are used interchangeably but when people say the DOM is working with an element it is actually working with a node that __represents__ that element.


### Caching DOM Queries
Methods that find elements in the DOM tree are called **DOM queries**.

Note: When you need to work with an element more than once, you should use a variable to store the result of this query. This saves the browser looking through the DOM tree to find the same element(s) again. It is known as **caching** the selection. Programmers would say that the variable stores a "reference" to the object in the DOM tree (it is storing the location of the node.)

When people talk about storing elements in variables, they are really storing the location of the element(s) within the DOM tree in a variable. The properties and methods of that element node work on the variable.


### Selecting an individual element node

> getElementById()
Selects an individual element given the value of its id attribute.
Note: this is always quickest and most efficient way to access an element since ID's can be repeated.

> querySelector()
Uses CSS selector syntax that would select one or more elements. This method returns only the **first** of the matching elements.


### Selecting multiple elements (known as a NodeList)

> getElementsByClassName()
Selects one or more elements given the value of their class attribute.
Note: this method is faster than querySelectorAll().

> getElementsByTagName()
Selects ALL elements on the page with a specified tag name.
Note: this method is faster than querySelectorAll().

> querySelectorAll()
Uses CSS Selector syntax to select one or more elements and returns all of those matches.

### Traversing between element nodes

parentNode

previousSibling

nextSibling

firstChild

lastChild


**NodeLists** When a DOM method **can** return more that one element, it returns a NodeList (even if it only finds one matching element). A Nodelist is a collection of element nodes. Each node is given an index number ( a number that starts at 0, just like arrays)

Note: Nodelists look like arrays and are numbered like arrays, but they are not actually arrays, they are a type of object called a **collection**.


### Live and Static NodeLists

There are times when you will want to work with the same selection of elements several times, so the NodeList can be stored in a variable and re-used  (rather than collecting the same elements again).

**Live NodeList**
When a script updates the page, the NodeList is updated at the same time. All methods starting with **getElementsBy** return a live NodeLists. Note: they are faster to generate than static NodeLists.

**Static NodeList**
When a script updates the page the node list is NOTE updated. **querySelectors** return static NodeLists. They reflect the document WHEN the query was made. If the script changes the content on the page the NodeList is NOT updated to reflect those changes.

###### Breaking down all four parts of the DOM selection method below:

```
document.getElementById('one')
```

**document** --> Refers to the document object. You always have to access individual elements via the document object.

**. (member operator)** --> The dot notation indicates that the method (on the right) is being applied to the node on the left side of the period.

**method** --> The getElementById() method indicates that you want to find the element based upon the value of its ID attribute.

**parameter** --> The method needs to know the value of the id attribute on the element you want. It is the parameter of the method.


### the item() Method

There are two ways to select an element form a NodeList:

1. the item() method
> var firstItem = elements.item(0);

2. array syntax
> var firstItem = elements[0];

Note: Array syntax is preferred over the item() method because it is faster. Before selecting a node form a NodeList, check that is contains nodes. If you repeatedly use the NodeList, store it in a variable.

### Steps for DOM selecting/updating

1. Find the element nodes
```
var elements = document.getElementsByClassName("soccer"); // finds "soccer" elements
```

2. conditional (optional)
```
if (elements.length > 2) { // if 3 or more are found
}
```

3. Select (inside if statement in this example )
```
var el = elements[2] // selects the third element in the NodeList
```

4. Update/change value (inside if statement in this example)
```
el.className = "basketball";
```


##### Update this section of the DOM notes next.

**The Document Object Model - DOM**
The only purpose of the html is for the browser to ingest it  and turn it into the DOM, if you want to some nothing with it after then you can manipulate it via the DOM API. HTML is parsed into a DOM " a string to a tree" that string is rendered to the DOM so it displays a certain way. Every web browser has something called the DOM, where DOM is an acronym for Document Object Model. The DOM is an API, where API is an acronym for Application Programming Interface. Simply put, an API is a way for programs to interact with each-other.

> Write JavaScript against the DOM API
    * Includes event handlers for clicks, key events, submit events
    * Creates and appends DOM elements
    * Uses event delegation to capture events from dynamically added elements
    * Finds existing elements by id and className in order to make changes
    * Mutates properties on existing DOM elements such as style, classNames

> Target, create, and manipulate DOM Elements
    * Creates and appends DOM elements
    * Finds existing elements by id and className in order to make changes
    * Mutates properties on existing DOM elements such as style, classNames

**DOM Elements | Node Tree**
How the DOM models the document:

The DOM models (represents) the document as an object.Objects are nice because programs can interact with them easily. It would be hard if we had to interact with the document by having our programs read the HTML or use computer vision to interact with the browser window. This isn't just any object, it is a special data structure known as a tree. The data structure gets its name because it can be visually represented to look like a real world tree: a tree has a trunk, the trunk has branches, each branch can have more branches. The data structure tree has a root node (trunk), the root node has nodes (branches), a node (branch) can have other nodes (branches). The file system is a tree. The root directory / is the root node (trunk). It contains several other directories, each of these is a node (branch). Each of those directories contain other directories (nodes).


Just like a directory:
* A node contained in another node is known as the child node.
* A node that contains another node is known as the parent node.

How the HTML maps to the tree:
1. The <html></html> tag becomes the root node.
2. It has 2 child nodes: <head></head>, <body></body
3. The <head></head> node has a child node: <title></title>.
4. The <body></body> node has 2 child nodes: <h1></h1>, <div></div>.
5. The <div></div> node has a child node: <p></p>.


**Selection/Traversal**

querySelector(“ “) - only returns the first match.
querySelectorAll(“ “) - returns the selected “nodelist”

firstChild & lastChild - example: selecting the first and/or last node. (li’s inside a ul)
parentNode & childNode - example: selecting the ul would be the parentNode of an li (which would be considered the childNode)
previousSibling & nextSibling - adjacent node elements on the same level, example li’s that are next to each other.
nodeValue is a little more confusing to use, but faster than innerHTML
innerHTML parses content as HTML and takes longer.
textContent uses straight text, does not parse HTML, and is faster.
innerText Takes styles into consideration. It won't get hidden text for instance.
createElement -
createTextNode -
removeChild -
appendChild -
.setAttribute -
type this is the name of the event
target (node) - this is the dom node where the event originated.
preventDefault - (function) This prevents any default behavior from occurring that the user agent (i.e. browser) might carry out in relation to the event (for example, preventing a click event on an <a> element from loading a new page).
load event:  fires on any resource that has finished loading (including any dependent resources). This could be an image, stylesheet, script, video, audio file, document or window.

Form Validation
New.js ← example form file

function getFormData() {
This selects all form inputs by queryselector
 var data = new FormData(document.querySelector("#submittedForm"));
This collects all the form data
function getFormData() {
This selects all form inputs by queryselector
 var data = new FormData(document.querySelector("#submittedForm"));

Returns the data from the form itself? For this return the "name:" is the data that it is getting and "nameInput" is the "name" that is on the actual form field itself.
 return {
       name: data.get("nameInput"),
       city: data.get("cityInput"),
       state: data.get("stateInput"),
       country: data.get("countryInput"),
       division: data.get("divisionInput"),
 };
}
   .then(response => response.json())
   .then(response => {
     // log
     console.log(response);
   }).catch(console.error);
}


Events
Events: actions or occurrences that happen in the system you are programming, which the system tells you amour so you can respond to them in some way if desired. For example if the user clicks a button on a webpage you mights what to respond to that action by displaying info.
Click Event: common DOM event fired by the browser when you click on something with your mouse.
Event Handler: the "onclick" handler property is equal to an anonymous function which contains the code we want the click event to run.
document.querySelector ("html").onclick - function () {};
(is equivalent to)
var myHTML = document.querySelector("html");
myHTML.onclick = function() {};


Inline event handlers (do NOT use)
<button onclick="bgChange()"> Press Me </button>
function bgChange() {
var newColor……
document.body.style.backgroundColor = bgChange;
}

addEventListener() / removeEventListener: functions similar way to the event handler properties but the syntax is different.
var btn = document.querySelector("button");
function bgChange() {
// some code
}
btn.addEventListener("click", bgChange);


Event Handler vs add/removeEventListener: Event handler properties have less power and options, but better cross browser compatibility. While add/removeEventListener are more powerful, but can also become more complex and are less supported by browsers. The main advantage to using add/removeEventListener is that you can add multiple listeners to the same type of element if required. You can also call these on an element multiple times with different functions specified in the second argument(they scale better) This would be impossible with event handler properties because any subsequent attempts to set a property will overwrite the earlier ones.
element.addEventListener(<event-name>, <callback>, <use-capture>);
event-name (string) This is the name or type of event that you would like to listen to. It could be any of the standard DOM events (click, mousedown, touchstart, transitionEnd, etc.) or even your own custom event name (we’ll touch on custom events later).
callback (function) This function gets called when the event happens. The event object, containing data about the event, is passed as the first argument.
* use-capture (boolean) This declares whether the callback should be fired in the “capture” phase.

Event Objects: inside of event handler functions you might see a parameter specified with a name such as event, eve, or e. This is called an event object and is automatically passed to the event handler to provide extra features and information.

function bgChange(e) {
    var newColor
     // some code
     console.log(e);
}
btn.addEventListener("click", bgChange);


Event Delegation & Bubbling: Bubbling allows us to take advantage of event delegation. This concept relies on the fact that id you want code to run when you clock any one of a large number of child elements, you can set the event listener on their parent and have the effect of the event listener bubble to each child, rather than having to set the event listener on every child individually. A good example is a series of listed items - if you want each one to "pop up" with a message when clicked, you can set the click event listener on the the parent ur and it will bubble to the list items.
Event Delegation: You can trigger an event on a parent by clicking on a child element for example.
Event Bubbling Visual Demo: https://codepen.io/BertoOrt/pen/GmmarX
<ul> - adding the click event listener to the ul will "bubble" down and apply to all the li's.
     <li> test </li>
 <li> test </li>
</ul>


The term **elements** & **node elements** are used interchangeably but when people say the DOM is working with an element it is actually working with a node that __represents__ that element.


### Caching DOM Queries
Methods that find elements in the DOM tree are called **DOM queries**.

Note: When you need to work with an element more than once, you should use a variable to store the result of this query. This saves the browser looking through the DOM tree to find the same element(s) again. It is known as **caching** the selection. Programmers would say that the variable stores a "reference" to the object in the DOM tree (it is storing the location of the node.)

When people talk about storing elements in variables, they are really storing the location of the element(s) within the DOM tree in a variable. The properties and methods of that element node work on the variable.


### Selecting an individual element node

> getElementById()
Selects an individual element given the value of its id attribute.
Note: this is always quickest and most efficient way to access an element since ID's can be repeated.

> querySelector()
Uses CSS selector syntax that would select one or more elements. This method returns only the **first** of the matching elements.


### Selecting multiple elements (known as a NodeList)

> getElementsByClassName()
Selects one or more elements given the value of their class attribute.
Note: this method is faster than querySelectorAll().

> getElementsByTagName()
Selects ALL elements on the page with a specified tag name.
Note: this method is faster than querySelectorAll().

> querySelectorAll()
Uses CSS Selector syntax to select one or more elements and returns all of those matches.

### Traversing between element nodes

parentNode

previousSibling

nextSibling

firstChild

lastChild


**NodeLists** When a DOM method **can** return more that one element, it returns a NodeList (even if it only finds one matching element). A Nodelist is a collection of element nodes. Each node is given an index number ( a number that starts at 0, just like arrays)

Note: Nodelists look like arrays and are numbered like arrays, but they are not actually arrays, they are a type of object called a **collection**.


### Live and Static NodeLists

There are times when you will want to work with the same selection of elements several times, so the NodeList can be stored in a variable and re-used  (rather than collecting the same elements again).

**Live NodeList**
When a script updates the page, the NodeList is updated at the same time. All methods starting with **getElementsBy** return a live NodeLists. Note: they are faster to generate than static NodeLists.

**Static NodeList**
When a script updates the page the node list is NOTE updated. **querySelectors** return static NodeLists. They reflect the document WHEN the query was made. If the script changes the content on the page the NodeList is NOT updated to reflect those changes.

###### Breaking down all four parts of the DOM selection method below:

```
document.getElementById('one')
```

**document** --> Refers to the document object. You always have to access individual elements via the document object.

**. (member operator)** --> The dot notation indicates that the method (on the right) is being applied to the node on the left side of the period.

**method** --> The getElementById() method indicates that you want to find the element based upon the value of its ID attribute.

**parameter** --> The method needs to know the value of the id attribute on the element you want. It is the parameter of the method.


### the item() Method

There are two ways to select an element form a NodeList:

1. the item() method
> var firstItem = elements.item(0);

2. array syntax
> var firstItem = elements[0];

Note: Array syntax is preferred over the item() method because it is faster. Before selecting a node form a NodeList, check that is contains nodes. If you repeatedly use the NodeList, store it in a variable.

### Steps for DOM selecting/updating

1. Find the element nodes
```
var elements = document.getElementsByClassName("soccer"); // finds "soccer" elements
```

2. conditional (optional)
```
if (elements.length > 2) { // if 3 or more are found
}
```

3. Select (inside if statement in this example )
```
var el = elements[2] // selects the third element in the NodeList
```

4. Update/change value (inside if statement in this example)
```
el.className = "basketball";
```


##### Update this section of the DOM notes next.

**The Document Object Model - DOM**
The only purpose of the html is for the browser to ingest it  and turn it into the DOM, if you want to some nothing with it after then you can manipulate it via the DOM API. HTML is parsed into a DOM " a string to a tree" that string is rendered to the DOM so it displays a certain way. Every web browser has something called the DOM, where DOM is an acronym for Document Object Model. The DOM is an API, where API is an acronym for Application Programming Interface. Simply put, an API is a way for programs to interact with each-other.

> Write JavaScript against the DOM API
    * Includes event handlers for clicks, key events, submit events
    * Creates and appends DOM elements
    * Uses event delegation to capture events from dynamically added elements
    * Finds existing elements by id and className in order to make changes
    * Mutates properties on existing DOM elements such as style, classNames

> Target, create, and manipulate DOM Elements
    * Creates and appends DOM elements
    * Finds existing elements by id and className in order to make changes
    * Mutates properties on existing DOM elements such as style, classNames

**DOM Elements | Node Tree**
How the DOM models the document:

The DOM models (represents) the document as an object.Objects are nice because programs can interact with them easily. It would be hard if we had to interact with the document by having our programs read the HTML or use computer vision to interact with the browser window. This isn't just any object, it is a special data structure known as a tree. The data structure gets its name because it can be visually represented to look like a real world tree: a tree has a trunk, the trunk has branches, each branch can have more branches. The data structure tree has a root node (trunk), the root node has nodes (branches), a node (branch) can have other nodes (branches). The file system is a tree. The root directory / is the root node (trunk). It contains several other directories, each of these is a node (branch). Each of those directories contain other directories (nodes).


Just like a directory:
* A node contained in another node is known as the child node.
* A node that contains another node is known as the parent node.

How the HTML maps to the tree:
1. The <html></html> tag becomes the root node.
2. It has 2 child nodes: <head></head>, <body></body
3. The <head></head> node has a child node: <title></title>.
4. The <body></body> node has 2 child nodes: <h1></h1>, <div></div>.
5. The <div></div> node has a child node: <p></p>.


**Selection/Traversal**

querySelector(“ “) - only returns the first match.
querySelectorAll(“ “) - returns the selected “nodelist”

firstChild & lastChild - example: selecting the first and/or last node. (li’s inside a ul)
parentNode & childNode - example: selecting the ul would be the parentNode of an li (which would be considered the childNode)
previousSibling & nextSibling - adjacent node elements on the same level, example li’s that are next to each other.
nodeValue is a little more confusing to use, but faster than innerHTML
innerHTML parses content as HTML and takes longer.
textContent uses straight text, does not parse HTML, and is faster.
innerText Takes styles into consideration. It won't get hidden text for instance.
createElement -
createTextNode -
removeChild -
appendChild -
.setAttribute -
type this is the name of the event
target (node) - this is the dom node where the event originated.
preventDefault - (function) This prevents any default behavior from occurring that the user agent (i.e. browser) might carry out in relation to the event (for example, preventing a click event on an <a> element from loading a new page).
load event:  fires on any resource that has finished loading (including any dependent resources). This could be an image, stylesheet, script, video, audio file, document or window.

Form Validation
New.js ← example form file

function getFormData() {
This selects all form inputs by queryselector
 var data = new FormData(document.querySelector("#submittedForm"));
This collects all the form data
function getFormData() {
This selects all form inputs by queryselector
 var data = new FormData(document.querySelector("#submittedForm"));

Returns the data from the form itself? For this return the "name:" is the data that it is getting and "nameInput" is the "name" that is on the actual form field itself.
 return {
       name: data.get("nameInput"),
       city: data.get("cityInput"),
       state: data.get("stateInput"),
       country: data.get("countryInput"),
       division: data.get("divisionInput"),
 };
}
   .then(response => response.json())
   .then(response => {
     // log
     console.log(response);
   }).catch(console.error);
}


Events
Events: actions or occurrences that happen in the system you are programming, which the system tells you amour so you can respond to them in some way if desired. For example if the user clicks a button on a webpage you mights what to respond to that action by displaying info.
Click Event: common DOM event fired by the browser when you click on something with your mouse.
Event Handler: the "onclick" handler property is equal to an anonymous function which contains the code we want the click event to run.
document.querySelector ("html").onclick - function () {};
(is equivalent to)
var myHTML = document.querySelector("html");
myHTML.onclick = function() {};


Inline event handlers (do NOT use)
<button onclick="bgChange()"> Press Me </button>
function bgChange() {
var newColor……
document.body.style.backgroundColor = bgChange;
}

addEventListener() / removeEventListener: functions similar way to the event handler properties but the syntax is different.
var btn = document.querySelector("button");
function bgChange() {
// some code
}
btn.addEventListener("click", bgChange);


Event Handler vs add/removeEventListener: Event handler properties have less power and options, but better cross browser compatibility. While add/removeEventListener are more powerful, but can also become more complex and are less supported by browsers. The main advantage to using add/removeEventListener is that you can add multiple listeners to the same type of element if required. You can also call these on an element multiple times with different functions specified in the second argument(they scale better) This would be impossible with event handler properties because any subsequent attempts to set a property will overwrite the earlier ones.
element.addEventListener(<event-name>, <callback>, <use-capture>);
event-name (string) This is the name or type of event that you would like to listen to. It could be any of the standard DOM events (click, mousedown, touchstart, transitionEnd, etc.) or even your own custom event name (we’ll touch on custom events later).
callback (function) This function gets called when the event happens. The event object, containing data about the event, is passed as the first argument.
* use-capture (boolean) This declares whether the callback should be fired in the “capture” phase.

Event Objects: inside of event handler functions you might see a parameter specified with a name such as event, eve, or e. This is called an event object and is automatically passed to the event handler to provide extra features and information.

function bgChange(e) {
    var newColor
     // some code
     console.log(e);
}
btn.addEventListener("click", bgChange);


Event Delegation & Bubbling: Bubbling allows us to take advantage of event delegation. This concept relies on the fact that id you want code to run when you clock any one of a large number of child elements, you can set the event listener on their parent and have the effect of the event listener bubble to each child, rather than having to set the event listener on every child individually. A good example is a series of listed items - if you want each one to "pop up" with a message when clicked, you can set the click event listener on the the parent ur and it will bubble to the list items.
Event Delegation: You can trigger an event on a parent by clicking on a child element for example.
Event Bubbling Visual Demo: https://codepen.io/BertoOrt/pen/GmmarX
<ul> - adding the click event listener to the ul will "bubble" down and apply to all the li's.
     <li> test </li>
 <li> test </li>
</ul>


The term **elements** & **node elements** are used interchangeably but when people say the DOM is working with an element it is actually working with a node that __represents__ that element.


### Caching DOM Queries
Methods that find elements in the DOM tree are called **DOM queries**.

Note: When you need to work with an element more than once, you should use a variable to store the result of this query. This saves the browser looking through the DOM tree to find the same element(s) again. It is known as **caching** the selection. Programmers would say that the variable stores a "reference" to the object in the DOM tree (it is storing the location of the node.)

When people talk about storing elements in variables, they are really storing the location of the element(s) within the DOM tree in a variable. The properties and methods of that element node work on the variable.


### Selecting an individual element node

> getElementById()
Selects an individual element given the value of its id attribute.
Note: this is always quickest and most efficient way to access an element since ID's can be repeated.

> querySelector()
Uses CSS selector syntax that would select one or more elements. This method returns only the **first** of the matching elements.


### Selecting multiple elements (known as a NodeList)

> getElementsByClassName()
Selects one or more elements given the value of their class attribute.
Note: this method is faster than querySelectorAll().

> getElementsByTagName()
Selects ALL elements on the page with a specified tag name.
Note: this method is faster than querySelectorAll().

> querySelectorAll()
Uses CSS Selector syntax to select one or more elements and returns all of those matches.

### Traversing between element nodes

parentNode

previousSibling

nextSibling

firstChild

lastChild


**NodeLists** When a DOM method **can** return more that one element, it returns a NodeList (even if it only finds one matching element). A Nodelist is a collection of element nodes. Each node is given an index number ( a number that starts at 0, just like arrays)

Note: Nodelists look like arrays and are numbered like arrays, but they are not actually arrays, they are a type of object called a **collection**.


### Live and Static NodeLists

There are times when you will want to work with the same selection of elements several times, so the NodeList can be stored in a variable and re-used  (rather than collecting the same elements again).

**Live NodeList**
When a script updates the page, the NodeList is updated at the same time. All methods starting with **getElementsBy** return a live NodeLists. Note: they are faster to generate than static NodeLists.

**Static NodeList**
When a script updates the page the node list is NOTE updated. **querySelectors** return static NodeLists. They reflect the document WHEN the query was made. If the script changes the content on the page the NodeList is NOT updated to reflect those changes.

###### Breaking down all four parts of the DOM selection method below:

```
document.getElementById('one')
```

**document** --> Refers to the document object. You always have to access individual elements via the document object.

**. (member operator)** --> The dot notation indicates that the method (on the right) is being applied to the node on the left side of the period.

**method** --> The getElementById() method indicates that you want to find the element based upon the value of its ID attribute.

**parameter** --> The method needs to know the value of the id attribute on the element you want. It is the parameter of the method.


### the item() Method

There are two ways to select an element form a NodeList:

1. the item() method
> var firstItem = elements.item(0);

2. array syntax
> var firstItem = elements[0];

Note: Array syntax is preferred over the item() method because it is faster. Before selecting a node form a NodeList, check that is contains nodes. If you repeatedly use the NodeList, store it in a variable.

### Steps for DOM selecting/updating

1. Find the element nodes
```
var elements = document.getElementsByClassName("soccer"); // finds "soccer" elements
```

2. conditional (optional)
```
if (elements.length > 2) { // if 3 or more are found
}
```

3. Select (inside if statement in this example )
```
var el = elements[2] // selects the third element in the NodeList
```

4. Update/change value (inside if statement in this example)
```
el.className = "basketball";
```


##### Update this section of the DOM notes next.

**The Document Object Model - DOM**
The only purpose of the html is for the browser to ingest it  and turn it into the DOM, if you want to some nothing with it after then you can manipulate it via the DOM API. HTML is parsed into a DOM " a string to a tree" that string is rendered to the DOM so it displays a certain way. Every web browser has something called the DOM, where DOM is an acronym for Document Object Model. The DOM is an API, where API is an acronym for Application Programming Interface. Simply put, an API is a way for programs to interact with each-other.

> Write JavaScript against the DOM API
    * Includes event handlers for clicks, key events, submit events
    * Creates and appends DOM elements
    * Uses event delegation to capture events from dynamically added elements
    * Finds existing elements by id and className in order to make changes
    * Mutates properties on existing DOM elements such as style, classNames

> Target, create, and manipulate DOM Elements
    * Creates and appends DOM elements
    * Finds existing elements by id and className in order to make changes
    * Mutates properties on existing DOM elements such as style, classNames

**DOM Elements | Node Tree**
How the DOM models the document:

The DOM models (represents) the document as an object.Objects are nice because programs can interact with them easily. It would be hard if we had to interact with the document by having our programs read the HTML or use computer vision to interact with the browser window. This isn't just any object, it is a special data structure known as a tree. The data structure gets its name because it can be visually represented to look like a real world tree: a tree has a trunk, the trunk has branches, each branch can have more branches. The data structure tree has a root node (trunk), the root node has nodes (branches), a node (branch) can have other nodes (branches). The file system is a tree. The root directory / is the root node (trunk). It contains several other directories, each of these is a node (branch). Each of those directories contain other directories (nodes).


Just like a directory:
* A node contained in another node is known as the child node.
* A node that contains another node is known as the parent node.

How the HTML maps to the tree:
1. The <html></html> tag becomes the root node.
2. It has 2 child nodes: <head></head>, <body></body
3. The <head></head> node has a child node: <title></title>.
4. The <body></body> node has 2 child nodes: <h1></h1>, <div></div>.
5. The <div></div> node has a child node: <p></p>.


**Selection/Traversal**

querySelector(“ “) - only returns the first match.
querySelectorAll(“ “) - returns the selected “nodelist”

firstChild & lastChild - example: selecting the first and/or last node. (li’s inside a ul)
parentNode & childNode - example: selecting the ul would be the parentNode of an li (which would be considered the childNode)
previousSibling & nextSibling - adjacent node elements on the same level, example li’s that are next to each other.
nodeValue is a little more confusing to use, but faster than innerHTML
innerHTML parses content as HTML and takes longer.
textContent uses straight text, does not parse HTML, and is faster.
innerText Takes styles into consideration. It won't get hidden text for instance.
createElement -
createTextNode -
removeChild -
appendChild -
.setAttribute -
type this is the name of the event
target (node) - this is the dom node where the event originated.
preventDefault - (function) This prevents any default behavior from occurring that the user agent (i.e. browser) might carry out in relation to the event (for example, preventing a click event on an <a> element from loading a new page).
load event:  fires on any resource that has finished loading (including any dependent resources). This could be an image, stylesheet, script, video, audio file, document or window.

Form Validation
New.js ← example form file

function getFormData() {
This selects all form inputs by queryselector
 var data = new FormData(document.querySelector("#submittedForm"));
This collects all the form data
function getFormData() {
This selects all form inputs by queryselector
 var data = new FormData(document.querySelector("#submittedForm"));

Returns the data from the form itself? For this return the "name:" is the data that it is getting and "nameInput" is the "name" that is on the actual form field itself.
 return {
       name: data.get("nameInput"),
       city: data.get("cityInput"),
       state: data.get("stateInput"),
       country: data.get("countryInput"),
       division: data.get("divisionInput"),
 };
}
   .then(response => response.json())
   .then(response => {
     // log
     console.log(response);
   }).catch(console.error);
}


Events
Events: actions or occurrences that happen in the system you are programming, which the system tells you amour so you can respond to them in some way if desired. For example if the user clicks a button on a webpage you mights what to respond to that action by displaying info.
Click Event: common DOM event fired by the browser when you click on something with your mouse.
Event Handler: the "onclick" handler property is equal to an anonymous function which contains the code we want the click event to run.
document.querySelector ("html").onclick - function () {};
(is equivalent to)
var myHTML = document.querySelector("html");
myHTML.onclick = function() {};


Inline event handlers (do NOT use)
<button onclick="bgChange()"> Press Me </button>
function bgChange() {
var newColor……
document.body.style.backgroundColor = bgChange;
}

addEventListener() / removeEventListener: functions similar way to the event handler properties but the syntax is different.
var btn = document.querySelector("button");
function bgChange() {
// some code
}
btn.addEventListener("click", bgChange);


Event Handler vs add/removeEventListener: Event handler properties have less power and options, but better cross browser compatibility. While add/removeEventListener are more powerful, but can also become more complex and are less supported by browsers. The main advantage to using add/removeEventListener is that you can add multiple listeners to the same type of element if required. You can also call these on an element multiple times with different functions specified in the second argument(they scale better) This would be impossible with event handler properties because any subsequent attempts to set a property will overwrite the earlier ones.
element.addEventListener(<event-name>, <callback>, <use-capture>);
event-name (string) This is the name or type of event that you would like to listen to. It could be any of the standard DOM events (click, mousedown, touchstart, transitionEnd, etc.) or even your own custom event name (we’ll touch on custom events later).
callback (function) This function gets called when the event happens. The event object, containing data about the event, is passed as the first argument.
* use-capture (boolean) This declares whether the callback should be fired in the “capture” phase.

Event Objects: inside of event handler functions you might see a parameter specified with a name such as event, eve, or e. This is called an event object and is automatically passed to the event handler to provide extra features and information.

function bgChange(e) {
    var newColor
     // some code
     console.log(e);
}
btn.addEventListener("click", bgChange);


Event Delegation & Bubbling: Bubbling allows us to take advantage of event delegation. This concept relies on the fact that id you want code to run when you clock any one of a large number of child elements, you can set the event listener on their parent and have the effect of the event listener bubble to each child, rather than having to set the event listener on every child individually. A good example is a series of listed items - if you want each one to "pop up" with a message when clicked, you can set the click event listener on the the parent ur and it will bubble to the list items.
Event Delegation: You can trigger an event on a parent by clicking on a child element for example.
Event Bubbling Visual Demo: https://codepen.io/BertoOrt/pen/GmmarX
<ul> - adding the click event listener to the ul will "bubble" down and apply to all the li's.
     <li> test </li>
 <li> test </li>
</ul>


The term **elements** & **node elements** are used interchangeably but when people say the DOM is working with an element it is actually working with a node that __represents__ that element.


### Caching DOM Queries
Methods that find elements in the DOM tree are called **DOM queries**.

Note: When you need to work with an element more than once, you should use a variable to store the result of this query. This saves the browser looking through the DOM tree to find the same element(s) again. It is known as **caching** the selection. Programmers would say that the variable stores a "reference" to the object in the DOM tree (it is storing the location of the node.)

When people talk about storing elements in variables, they are really storing the location of the element(s) within the DOM tree in a variable. The properties and methods of that element node work on the variable.


### Selecting an individual element node

> getElementById()
Selects an individual element given the value of its id attribute.
Note: this is always quickest and most efficient way to access an element since ID's can be repeated.

> querySelector()
Uses CSS selector syntax that would select one or more elements. This method returns only the **first** of the matching elements.


### Selecting multiple elements (known as a NodeList)

> getElementsByClassName()
Selects one or more elements given the value of their class attribute.
Note: this method is faster than querySelectorAll().

> getElementsByTagName()
Selects ALL elements on the page with a specified tag name.
Note: this method is faster than querySelectorAll().

> querySelectorAll()
Uses CSS Selector syntax to select one or more elements and returns all of those matches.

### Traversing between element nodes

parentNode

previousSibling

nextSibling

firstChild

lastChild


**NodeLists** When a DOM method **can** return more that one element, it returns a NodeList (even if it only finds one matching element). A Nodelist is a collection of element nodes. Each node is given an index number ( a number that starts at 0, just like arrays)

Note: Nodelists look like arrays and are numbered like arrays, but they are not actually arrays, they are a type of object called a **collection**.


### Live and Static NodeLists

There are times when you will want to work with the same selection of elements several times, so the NodeList can be stored in a variable and re-used  (rather than collecting the same elements again).

**Live NodeList**
When a script updates the page, the NodeList is updated at the same time. All methods starting with **getElementsBy** return a live NodeLists. Note: they are faster to generate than static NodeLists.

**Static NodeList**
When a script updates the page the node list is NOTE updated. **querySelectors** return static NodeLists. They reflect the document WHEN the query was made. If the script changes the content on the page the NodeList is NOT updated to reflect those changes.

###### Breaking down all four parts of the DOM selection method below:

```
document.getElementById('one')
```

**document** --> Refers to the document object. You always have to access individual elements via the document object.

**. (member operator)** --> The dot notation indicates that the method (on the right) is being applied to the node on the left side of the period.

**method** --> The getElementById() method indicates that you want to find the element based upon the value of its ID attribute.

**parameter** --> The method needs to know the value of the id attribute on the element you want. It is the parameter of the method.


### the item() Method

There are two ways to select an element form a NodeList:

1. the item() method
> var firstItem = elements.item(0);

2. array syntax
> var firstItem = elements[0];

Note: Array syntax is preferred over the item() method because it is faster. Before selecting a node form a NodeList, check that is contains nodes. If you repeatedly use the NodeList, store it in a variable.

### Steps for DOM selecting/updating

1. Find the element nodes
```
var elements = document.getElementsByClassName("soccer"); // finds "soccer" elements
```

2. conditional (optional)
```
if (elements.length > 2) { // if 3 or more are found
}
```

3. Select (inside if statement in this example )
```
var el = elements[2] // selects the third element in the NodeList
```

4. Update/change value (inside if statement in this example)
```
el.className = "basketball";
```


##### Update this section of the DOM notes next.

**The Document Object Model - DOM**
The only purpose of the html is for the browser to ingest it  and turn it into the DOM, if you want to some nothing with it after then you can manipulate it via the DOM API. HTML is parsed into a DOM " a string to a tree" that string is rendered to the DOM so it displays a certain way. Every web browser has something called the DOM, where DOM is an acronym for Document Object Model. The DOM is an API, where API is an acronym for Application Programming Interface. Simply put, an API is a way for programs to interact with each-other.

> Write JavaScript against the DOM API
    * Includes event handlers for clicks, key events, submit events
    * Creates and appends DOM elements
    * Uses event delegation to capture events from dynamically added elements
    * Finds existing elements by id and className in order to make changes
    * Mutates properties on existing DOM elements such as style, classNames

> Target, create, and manipulate DOM Elements
    * Creates and appends DOM elements
    * Finds existing elements by id and className in order to make changes
    * Mutates properties on existing DOM elements such as style, classNames

**DOM Elements | Node Tree**
How the DOM models the document:

The DOM models (represents) the document as an object.Objects are nice because programs can interact with them easily. It would be hard if we had to interact with the document by having our programs read the HTML or use computer vision to interact with the browser window. This isn't just any object, it is a special data structure known as a tree. The data structure gets its name because it can be visually represented to look like a real world tree: a tree has a trunk, the trunk has branches, each branch can have more branches. The data structure tree has a root node (trunk), the root node has nodes (branches), a node (branch) can have other nodes (branches). The file system is a tree. The root directory / is the root node (trunk). It contains several other directories, each of these is a node (branch). Each of those directories contain other directories (nodes).


Just like a directory:
* A node contained in another node is known as the child node.
* A node that contains another node is known as the parent node.

How the HTML maps to the tree:
1. The <html></html> tag becomes the root node.
2. It has 2 child nodes: <head></head>, <body></body
3. The <head></head> node has a child node: <title></title>.
4. The <body></body> node has 2 child nodes: <h1></h1>, <div></div>.
5. The <div></div> node has a child node: <p></p>.


**Selection/Traversal**

querySelector(“ “) - only returns the first match.
querySelectorAll(“ “) - returns the selected “nodelist”

firstChild & lastChild - example: selecting the first and/or last node. (li’s inside a ul)
parentNode & childNode - example: selecting the ul would be the parentNode of an li (which would be considered the childNode)
previousSibling & nextSibling - adjacent node elements on the same level, example li’s that are next to each other.
nodeValue is a little more confusing to use, but faster than innerHTML
innerHTML parses content as HTML and takes longer.
textContent uses straight text, does not parse HTML, and is faster.
innerText Takes styles into consideration. It won't get hidden text for instance.
createElement -
createTextNode -
removeChild -
appendChild -
.setAttribute -
type this is the name of the event
target (node) - this is the dom node where the event originated.
preventDefault - (function) This prevents any default behavior from occurring that the user agent (i.e. browser) might carry out in relation to the event (for example, preventing a click event on an <a> element from loading a new page).
load event:  fires on any resource that has finished loading (including any dependent resources). This could be an image, stylesheet, script, video, audio file, document or window.

Form Validation
New.js ← example form file

function getFormData() {
This selects all form inputs by queryselector
 var data = new FormData(document.querySelector("#submittedForm"));
This collects all the form data
function getFormData() {
This selects all form inputs by queryselector
 var data = new FormData(document.querySelector("#submittedForm"));

Returns the data from the form itself? For this return the "name:" is the data that it is getting and "nameInput" is the "name" that is on the actual form field itself.
 return {
       name: data.get("nameInput"),
       city: data.get("cityInput"),
       state: data.get("stateInput"),
       country: data.get("countryInput"),
       division: data.get("divisionInput"),
 };
}
   .then(response => response.json())
   .then(response => {
     // log
     console.log(response);
   }).catch(console.error);
}


Events
Events: actions or occurrences that happen in the system you are programming, which the system tells you amour so you can respond to them in some way if desired. For example if the user clicks a button on a webpage you mights what to respond to that action by displaying info.
Click Event: common DOM event fired by the browser when you click on something with your mouse.
Event Handler: the "onclick" handler property is equal to an anonymous function which contains the code we want the click event to run.
document.querySelector ("html").onclick - function () {};
(is equivalent to)
var myHTML = document.querySelector("html");
myHTML.onclick = function() {};


Inline event handlers (do NOT use)
<button onclick="bgChange()"> Press Me </button>
function bgChange() {
var newColor……
document.body.style.backgroundColor = bgChange;
}

addEventListener() / removeEventListener: functions similar way to the event handler properties but the syntax is different.
var btn = document.querySelector("button");
function bgChange() {
// some code
}
btn.addEventListener("click", bgChange);


Event Handler vs add/removeEventListener: Event handler properties have less power and options, but better cross browser compatibility. While add/removeEventListener are more powerful, but can also become more complex and are less supported by browsers. The main advantage to using add/removeEventListener is that you can add multiple listeners to the same type of element if required. You can also call these on an element multiple times with different functions specified in the second argument(they scale better) This would be impossible with event handler properties because any subsequent attempts to set a property will overwrite the earlier ones.
element.addEventListener(<event-name>, <callback>, <use-capture>);
event-name (string) This is the name or type of event that you would like to listen to. It could be any of the standard DOM events (click, mousedown, touchstart, transitionEnd, etc.) or even your own custom event name (we’ll touch on custom events later).
callback (function) This function gets called when the event happens. The event object, containing data about the event, is passed as the first argument.
* use-capture (boolean) This declares whether the callback should be fired in the “capture” phase.

Event Objects: inside of event handler functions you might see a parameter specified with a name such as event, eve, or e. This is called an event object and is automatically passed to the event handler to provide extra features and information.

function bgChange(e) {
    var newColor
     // some code
     console.log(e);
}
btn.addEventListener("click", bgChange);


Event Delegation & Bubbling: Bubbling allows us to take advantage of event delegation. This concept relies on the fact that id you want code to run when you clock any one of a large number of child elements, you can set the event listener on their parent and have the effect of the event listener bubble to each child, rather than having to set the event listener on every child individually. A good example is a series of listed items - if you want each one to "pop up" with a message when clicked, you can set the click event listener on the the parent ur and it will bubble to the list items.
Event Delegation: You can trigger an event on a parent by clicking on a child element for example.
Event Bubbling Visual Demo: https://codepen.io/BertoOrt/pen/GmmarX
<ul> - adding the click event listener to the ul will "bubble" down and apply to all the li's.
     <li> test </li>
 <li> test </li>
</ul>


}
btn.addEventListener("click", bgChange);


Event Delegation & Bubbling: Bubbling allows us to take advantage of event delegation. This concept relies on the fact that id you want code to run when you clock any one of a large number of child elements, you can set the event listener on their parent and have the effect of the event listener bubble to each child, rather than having to set the event listener on every child individually. A good example is a series of listed items - if you want each one to "pop up" with a message when clicked, you can set the click event listener on the the parent ur and it will bubble to the list items.
Event Delegation: You can trigger an event on a parent by clicking on a child element for example.
Event Bubbling Visual Demo: https://codepen.io/BertoOrt/pen/GmmarX
<ul> - adding the click event listener to the ul will "bubble" down and apply to all the li's.
     <li> test </li>
 <li> test </li>
</ul>



Event Delegation & Bubbling: Bubbling allows us to take advantage of event delegation. This concept relies on the fact that id you want code to run when you clock any one of a large number of child elements, you can set the event listener on their parent and have the effect of the event listener bubble to each child, rather than having to set the event listener on every child individually. A good example is a series of listed items - if you want each one to "pop up" with a message when clicked, you can set the click event listener on the the parent ur and it will bubble to the list items.
Event Delegation: You can trigger an event on a parent by clicking on a child element for example.
Event Bubbling Visual Demo: https://codepen.io/BertoOrt/pen/GmmarX
<ul> - adding the click event listener to the ul will "bubble" down and apply to all the li's.
     <li> test </li>
 <li> test </li>
</ul>


### Selecting an individual element node

> getElementById()
Selects an individual element given the value of its id attribute.
Note: this is always quickest and most efficient way to access an element since ID's can be repeated.

> querySelector()
Uses CSS selector syntax that would select one or more elements. This method returns only the **first** of the matching elements.


### Selecting multiple elements (known as a NodeList)

> getElementsByClassName()
Selects one or more elements given the value of their class attribute.
Note: this method is faster than querySelectorAll().

> getElementsByTagName()
Selects ALL elements on the page with a specified tag name.
Note: this method is faster than querySelectorAll().

> querySelectorAll()
Uses CSS Selector syntax to select one or more elements and returns all of those matches.

### Traversing between element nodes

parentNode

previousSibling

nextSibling

firstChild

lastChild


**NodeLists** When a DOM method **can** return more that one element, it returns a NodeList (even if it only finds one matching element). A Nodelist is a collection of element nodes. Each node is given an index number ( a number that starts at 0, just like arrays)

Note: Nodelists look like arrays and are numbered like arrays, but they are not actually arrays, they are a type of object called a **collection**.


### Live and Static NodeLists

There are times when you will want to work with the same selection of elements several times, so the NodeList can be stored in a variable and re-used  (rather than collecting the same elements again).

**Live NodeList**
When a script updates the page, the NodeList is updated at the same time. All methods starting with **getElementsBy** return a live NodeLists. Note: they are faster to generate than static NodeLists.

**Static NodeList**
When a script updates the page the node list is NOTE updated. **querySelectors** return static NodeLists. They reflect the document WHEN the query was made. If the script changes the content on the page the NodeList is NOT updated to reflect those changes.

###### Breaking down all four parts of the DOM selection method below:

```
document.getElementById('one')
```

**document** --> Refers to the document object. You always have to access individual elements via the document object.

**. (member operator)** --> The dot notation indicates that the method (on the right) is being applied to the node on the left side of the period.

**method** --> The getElementById() method indicates that you want to find the element based upon the value of its ID attribute.

**parameter** --> The method needs to know the value of the id attribute on the element you want. It is the parameter of the method.


### the item() Method

There are two ways to select an element form a NodeList:

1. the item() method
> var firstItem = elements.item(0);

2. array syntax
> var firstItem = elements[0];

Note: Array syntax is preferred over the item() method because it is faster. Before selecting a node form a NodeList, check that is contains nodes. If you repeatedly use the NodeList, store it in a variable.

### Steps for DOM selecting/updating

1. Find the element nodes
```
var elements = document.getElementsByClassName("soccer"); // finds "soccer" elements
```

2. conditional (optional)
```
if (elements.length > 2) { // if 3 or more are found
}
```

3. Select (inside if statement in this example )
```
var el = elements[2] // selects the third element in the NodeList
```

4. Update/change value (inside if statement in this example)
```
el.className = "basketball";
```


##### Update this section of the DOM notes next.

**The Document Object Model - DOM**
The only purpose of the html is for the browser to ingest it  and turn it into the DOM, if you want to some nothing with it after then you can manipulate it via the DOM API. HTML is parsed into a DOM " a string to a tree" that string is rendered to the DOM so it displays a certain way. Every web browser has something called the DOM, where DOM is an acronym for Document Object Model. The DOM is an API, where API is an acronym for Application Programming Interface. Simply put, an API is a way for programs to interact with each-other.

> Write JavaScript against the DOM API
    * Includes event handlers for clicks, key events, submit events
    * Creates and appends DOM elements
    * Uses event delegation to capture events from dynamically added elements
    * Finds existing elements by id and className in order to make changes
    * Mutates properties on existing DOM elements such as style, classNames

> Target, create, and manipulate DOM Elements
    * Creates and appends DOM elements
    * Finds existing elements by id and className in order to make changes
    * Mutates properties on existing DOM elements such as style, classNames

**DOM Elements | Node Tree**
How the DOM models the document:

The DOM models (represents) the document as an object.Objects are nice because programs can interact with them easily. It would be hard if we had to interact with the document by having our programs read the HTML or use computer vision to interact with the browser window. This isn't just any object, it is a special data structure known as a tree. The data structure gets its name because it can be visually represented to look like a real world tree: a tree has a trunk, the trunk has branches, each branch can have more branches. The data structure tree has a root node (trunk), the root node has nodes (branches), a node (branch) can have other nodes (branches). The file system is a tree. The root directory / is the root node (trunk). It contains several other directories, each of these is a node (branch). Each of those directories contain other directories (nodes).


Just like a directory:
* A node contained in another node is known as the child node.
* A node that contains another node is known as the parent node.

How the HTML maps to the tree:
1. The <html></html> tag becomes the root node.
2. It has 2 child nodes: <head></head>, <body></body
3. The <head></head> node has a child node: <title></title>.
4. The <body></body> node has 2 child nodes: <h1></h1>, <div></div>.
5. The <div></div> node has a child node: <p></p>.


**Selection/Traversal**

querySelector(“ “) - only returns the first match.
querySelectorAll(“ “) - returns the selected “nodelist”

firstChild & lastChild - example: selecting the first and/or last node. (li’s inside a ul)
parentNode & childNode - example: selecting the ul would be the parentNode of an li (which would be considered the childNode)
previousSibling & nextSibling - adjacent node elements on the same level, example li’s that are next to each other.
nodeValue is a little more confusing to use, but faster than innerHTML
innerHTML parses content as HTML and takes longer.
textContent uses straight text, does not parse HTML, and is faster.
innerText Takes styles into consideration. It won't get hidden text for instance.
createElement -
createTextNode -
removeChild -
appendChild -
.setAttribute -
type this is the name of the event
target (node) - this is the dom node where the event originated.
preventDefault - (function) This prevents any default behavior from occurring that the user agent (i.e. browser) might carry out in relation to the event (for example, preventing a click event on an <a> element from loading a new page).
load event:  fires on any resource that has finished loading (including any dependent resources). This could be an image, stylesheet, script, video, audio file, document or window.

Form Validation
New.js ← example form file

function getFormData() {
This selects all form inputs by queryselector
 var data = new FormData(document.querySelector("#submittedForm"));
This collects all the form data
function getFormData() {
This selects all form inputs by queryselector
 var data = new FormData(document.querySelector("#submittedForm"));

Returns the data from the form itself? For this return the "name:" is the data that it is getting and "nameInput" is the "name" that is on the actual form field itself.
 return {
       name: data.get("nameInput"),
       city: data.get("cityInput"),
       state: data.get("stateInput"),
       country: data.get("countryInput"),
       division: data.get("divisionInput"),
 };
}
   .then(response => response.json())
   .then(response => {
     // log
     console.log(response);
   }).catch(console.error);
}


Events
Events: actions or occurrences that happen in the system you are programming, which the system tells you amour so you can respond to them in some way if desired. For example if the user clicks a button on a webpage you mights what to respond to that action by displaying info.
Click Event: common DOM event fired by the browser when you click on something with your mouse.
Event Handler: the "onclick" handler property is equal to an anonymous function which contains the code we want the click event to run.
document.querySelector ("html").onclick - function () {};
(is equivalent to)
var myHTML = document.querySelector("html");
myHTML.onclick = function() {};


Inline event handlers (do NOT use)
<button onclick="bgChange()"> Press Me </button>
function bgChange() {
var newColor……
document.body.style.backgroundColor = bgChange;
}

addEventListener() / removeEventListener: functions similar way to the event handler properties but the syntax is different.
var btn = document.querySelector("button");
function bgChange() {
// some code
}
btn.addEventListener("click", bgChange);


Event Handler vs add/removeEventListener: Event handler properties have less power and options, but better cross browser compatibility. While add/removeEventListener are more powerful, but can also become more complex and are less supported by browsers. The main advantage to using add/removeEventListener is that you can add multiple listeners to the same type of element if required. You can also call these on an element multiple times with different functions specified in the second argument(they scale better) This would be impossible with event handler properties because any subsequent attempts to set a property will overwrite the earlier ones.
element.addEventListener(<event-name>, <callback>, <use-capture>);
event-name (string) This is the name or type of event that you would like to listen to. It could be any of the standard DOM events (click, mousedown, touchstart, transitionEnd, etc.) or even your own custom event name (we’ll touch on custom events later).
callback (function) This function gets called when the event happens. The event object, containing data about the event, is passed as the first argument.
* use-capture (boolean) This declares whether the callback should be fired in the “capture” phase.

Event Objects: inside of event handler functions you might see a parameter specified with a name such as event, eve, or e. This is called an event object and is automatically passed to the event handler to provide extra features and information.

function bgChange(e) {
    var newColor
     // some code
     console.log(e);
}
btn.addEventListener("click", bgChange);


Event Delegation & Bubbling: Bubbling allows us to take advantage of event delegation. This concept relies on the fact that id you want code to run when you clock any one of a large number of child elements, you can set the event listener on their parent and have the effect of the event listener bubble to each child, rather than having to set the event listener on every child individually. A good example is a series of listed items - if you want each one to "pop up" with a message when clicked, you can set the click event listener on the the parent ur and it will bubble to the list items.
Event Delegation: You can trigger an event on a parent by clicking on a child element for example.
Event Bubbling Visual Demo: https://codepen.io/BertoOrt/pen/GmmarX
<ul> - adding the click event listener to the ul will "bubble" down and apply to all the li's.
     <li> test </li>
 <li> test </li>
</ul>

