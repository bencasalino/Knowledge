June
6/11 - Added Normalize CSS resets , border box sizing more css
6/12 - VsCode Updates




Run-time vs Write-time (python vs c++)
Compiled languages vs interpreted
Strongly Typed vs loosely typed
Type conversion vs type coercion
procedural vs OOP




VsCode Spell Checker Extension

Use CMD + . when selected on a word to reveal suggestions.





"I'm coding like a champ".length > 10;
Checks if the string is greater than a length of 10. via boolean
answer: true

The more you know:
You are doing what's called "debugging," a term popularized by Grace Hopper when she literally removed a moth from her computer.


<a name="content"></a> ==$0
When inspecting an element in the browser, the ==$0 can be used as a reference to that element by typing $0 in the same console.
Selecting the element is what sets it to $0. Note: in React for example we can use $r.
$0
<a name=​"content">​</a>​

Can also be chained.

$0.name
"content"

To see all properties available on a selected DOM node.

console.dir($0)



DOM
grabbing InnerHTML vs innerText

innerHTML -->  <span> test </span>
innerText --> test



Substring Selection:
console.log("January".substring(0, 3));
console.log("Melbourne is great".substring(0, 12));
console.log("Hamburgers".substring(3,10));

Returns:
Jan
Melbourne is
burgers



## Express:
Express is a Node module, so in order to use it, we will need to import it into our program file. To create a server, the imported express function must be invoked.
```
const express = require('express');
const app = express();
```

On the first line, we import the Express library with require. When invoked on the second line, it returns an instance of an Express application. This application can then be used to start a server and specify server behavior.

The purpose of a server is to listen for requests, perform whatever action is required to satisfy the request, and then return a response.

In order for our server to start responding, we have to tell the server where to listen for new requests by providing a port number argument to a method called **app.listen()**. The server will then listen on the specified port and respond to any requests that come into it.

The second argument is a callback function that will be called once the server is running and ready to receive responses.

```
const PORT = 4001;
app.listen(PORT, () => {
  console.log(`Server is listening on port ${PORT}`);
});
```


Simple Express Example:
```
// Import the express library here
const express = require('express');

// Instantiate the app here
const app = express();

// define the port
const PORT = process.env.PORT || 4001;

// Invoke the app's `.listen()` method below:
app.listen(PORT, () => {
  console.log(`Server is listening on port ${PORT}`);
});
```