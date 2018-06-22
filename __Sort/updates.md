https://docs.google.com/document/d/1Se-JP51ZAttkX2NFQzR-vtlD3cJakGLQEyUKWTNTP_0/edit
Old Galvanize Notes - sort these frist ( notes from eloquent js in here too! )

define:
Run-time vs Write-time (python vs c++)
Compiled languages vs interpreted
Strongly Typed vs loosely typed
Type conversion vs type coercion
procedural vs OOP

updates notes on how module exports works with data

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

innerHTML --> <span> test </span>
innerText --> test

Substring Selection:
console.log("January".substring(0, 3));
console.log("Melbourne is great".substring(0, 12));
console.log("Hamburgers".substring(3,10));

Returns:
Jan
Melbourne is
burgers
