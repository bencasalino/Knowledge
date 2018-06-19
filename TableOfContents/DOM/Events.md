# Event Types

---

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

---

###### Event Handling

1.  Select the element node(s) you want the script to respond to.
2.  Indicate which event on the selected node(s) will trigger the response. Programmers often call this **binding** an event to a DOM node.
3.  State the code you want to run when the event occurs.

---

##### Three ways to bind an event to an element.

1.  HTML Event handlers - Early versions of HTML included a set of attributes that could respond to the events on the element they were added to.

```
 <a onclick="hide()"> </a>
```

**NOTE:** This method is of event handling is no longer used because it;s better to separate the JS from the HTML however it is good to know and may be seen in older legacy code.

---

2.  Traditional DOM event handlers
    DOM event handlers were introduced in the original specification for the DOM. They are considered better than HTML event handlers because of the separation between HTML and JS.

**NOTE:** The main drawback is that you can only attach a single function to any event.

ex: The submit form event of a form cannot trigger one function that checks the contents of the form, and a second to submit the form data if it passes the check. As a result of this limitation if more than one script is used on the same page, and both scripts respond to the same evert, then one or both of the scripts may not work as intended.

---

3.  Event Listeners - introduced in 2000 and are now the favored way of handling events.
    Syntax is different but a single event listener can trigger multiple functions.

---

#### Using DOM Event handlers

1.

```
function checkUserName() {                                   // declare the function
  var elMsg = document.getElementById("feedback");           // get feedback element
  if (this.value.length < 5 ) {                              // if user name is too short
    elMsg.textContent = "username must be 5 chars or more";  // set message
  } else {                                                   // otherwise
    elMsg.textContent = "";                                  // clear message
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

- functionName --> code, name of the function to call

- [Boolean] --> "event flow" indicated something called capture and is usually set to false.

Example Event Listener: (same as above example but step 3 is different)

```
elUserName.addEventListener('blur', checkUserName, false);
```

---

##### Using parameters with Event Handlers and Listeners.

**NOTE:** Because you cannot have parentheses after the function na,e in event handlers or listeners, passing arguments requires a workaround.

When the interpreter sees the parentheses after a function call, it runs the code straight away. In in an event **handler**, you want it to wait until the event triggers it.

Therefore, if you need to pass arguments to a function that is called by an event handler or listener, you wrap the function call in an **anonymous function**.

```
var elUserName = document.getElementById('username');        // get username input
var elMsg = document.getElementById('feedback);              // get feedback element



function checkUserName(minLength) {                          // declare the function

  if (elUserName.value.length < minLength) {                 // if user name is too short
  // set error message
    elMsg.textContent = "username must be 5 chars or more";  // set message
  } else {                                                   // otherwise
    elMsg.innerHTML = "";                                    // clear message
    }
}

elUserName.addEventListener('blur', function() {             // when it loses focus
  checkUserName(5);                                          // pass arguments here
})
```

### Event Flow

HTML Elements nest inside other elements. If you hover or click on a link, you will also be hovering or clicking on its parent elements.

**NOTE:** The flow of events on really matters when your code has event handlers on an element **AND** one of its ancestor or descendant selectors.

#### Event Bubbling (default)

The event starts at the **most** specific node and "flows outwards" to the least specific one. THis is the default type of event flow.

#### Event Capturing

The event starts at the **least** specific node and flows inward to the most specific one.

---

## Events Summary

Events are the browser's way of indicating when something has happened (such as when a page has finished loading or a button has been clicked).

Binding is the process of stating which event you are waiting to happen, and which element you are waiting for that event to happen upon.

You can use event delegation to monitor for events that happen on all of the children of an element.

---

#Event Object
When an event occurs the event object tells you the information about the event and the element it happened upon. When the event object is passed into a function, it is often given the parameter name **e**.

Properties:
target --> The target of the event.
type --> The type of event that was fired.

Method:
preventDefault() --> Cancel the behavior of the event (if it can be cancelled).
stopPropagation() --> stops the event from bubbling or capturing any further.

### Event Delegation

Creating event listeners for a lot of elements can sloe down a pagem but event flow allows you to listen for an event on a parent element. Because events affect containing elements due to event flow, you CAN place handlers on the containing element and use the "event object's target property" to find which of its children the event happens on.

By attaching an event listener to the containing element, you are only responding to one element (rather than having an event handler on each child element.)
