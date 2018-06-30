#JSON

Because properties only grasp their value, rather than contain it, objects and arrays are stored in the computer’s memory as sequences of bits holding the addresses—the place in memory—of their contents. So an array with another array inside of it consists of (at least) one memory region for the inner array, and another for the outer array, containing (among other things) a binary number that represents the position of the inner array.

If you want to save data in a file for later or send it to another computer over the network, you have to somehow convert these tangles of memory addresses to a description that can be stored or sent. You could send over your entire computer memory along with the address of the value you’re interested in, I suppose, but that doesn’t seem like the best approach.

What we can do is serialize the data. That means it is converted into a flat description. A popular serialization format is called JSON (pronounced “Jason”), which stands for JavaScript Object Notation. It is widely used as a data storage and communication format on the Web, even in languages other than JavaScript.

JSON looks similar to JavaScript’s way of writing arrays and objects, with a few restrictions. All property names have to be surrounded by double quotes, and only simple data expressions are allowed—no function calls, bindings, or anything that involves actual computation. Comments are not allowed in JSON.

---

A journal entry might look like this when represented as JSON data:

```
{
"squirrel": false,
"events": ["work", "touched tree", "pizza", "running"]
}
```

JavaScript gives us the functions **JSON.stringify** and **JSON.parse** to convert data to and from this format. The first takes a JavaScript value and returns a JSON-encoded string. The second takes such a string and converts it to the value it encodes.

```
let string = JSON.stringify({squirrel: false,
events: ["weekend"]});

console.log(string);
// → {"squirrel":false,"events":["weekend"]}

console.log(JSON.parse(string).events);
// → ["weekend"]
```

Define:

> JSON.stringify()

> JSON.parse
