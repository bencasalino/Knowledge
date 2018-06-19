#### Event Types

#### UI Events

- load
- unload
- error
- resize
- scroll

#### Keyboard Events

- keydown
- keyup
- keypress

#### Mouse Events

- click
- dbclick
- mousedown
- mouseup
- mouseover
- mouseout

#### Focus Events

- focus / focusin
- blur / focusout

#### Form Events

- input
- change
- submit
- reset
- cut
- copy
- paste
- select

#### Mutation Events

- DOMSubtreeModifies
- DOMNodeInserted
- DOMNodeRemoved

###### Event Handling

1.  Select the element node(s) you want the script to respond to.
2.  Indicate which event on the selected node(s) will trigger the response. Programmers often call this **binding** an event to a DOM node.
3.  State the code you want to run when the event occurs.

##### Three ways to bind an event to an element.

1.  HTML Event handlers - Early versions of HTML included a set of attributes that could respond to the events on the element they were added to.
    > ex: <a onclick="hide()"> </a>

**NOTE:** This method is of event handling is no longer used because it;s better to separate the JS from the HTML however it is good to know and may be seen in older legacy code.

2.  Traditional DOM event handlers
    DOM event handlers were introduced in the original specification for the DOM. They are considered better than HTML event handlers because of the separation between HTML and JS.

**NOTE:** The main drawback is that you can only attach a single function to any event.

ex: The submit form event of a form cannot trigger one function that checks the contents of the form, and a second to submit the form data if it passes the check. As a result of this limitation if more than one script is used on the same page, and both scripts respond to the same evert, then one or both of the scripts may not work as intended.

3.  Event Listeners - introduced in 2000 and are now the favored way of handling events.
    Syntax is different but a single event listener can trigger multiple functions.

    ***

#### Using DOM Event handlers

1.

```
function checkUserName() {           // declare the function
  var elMsg = document.getElementById("feedback"); // get feedback element
  if (this.value.length < 5 ) {      // if user name is too short
    elMsg.textContent = "username must be 5 chars or more";  // set message
  } else {                             // otherwise
    elMsg.textContent = "";            // clear message
    }
}
```

2.

```
var elUserName - document.getElementById("username"); // get username input
```

3.

```
elUserName.onblur = checkUserName // when it loses focus call checkUserName()
```

---

#### Using Event Listeners

```
element.addEventListener('event',functionName[, boolean]);
```

- element --> DOM element node to target.

- 'event' --> event to bind node(s) to in quote marks.

- fucntionName --> code, name of the function to call

- [Boolean] --> "event flow" indicated something called capture and is usually set to false.

Example Event Listener: (same as above example but step 3 is different)

```
elUserName.addEventListener('blur', checkUserName, false);
```
