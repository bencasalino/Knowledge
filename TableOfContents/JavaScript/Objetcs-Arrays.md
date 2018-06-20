**Objects** allow us to group values—including other objects—to build more complex structures.

Properties whose names aren’t valid binding names or valid numbers have to be quoted. (ex: "touched tree")

```
let descriptions = {
  work: "Went to work",
  "touched tree": "Touched a tree"
};
```

This means that braces have two meanings in JavaScript.

1.  At the start of a statement, they start a block of statements.

2.  In any other position, they describe an object.

**NOTE:**Fortunately, it is rarely useful to start a statement with an object in braces, so the ambiguity between these two is not much of a problem.

###### Properties

We’ve seen a few suspicious-looking expressions like myString.length (to get the length of a string) and Math.max (the maximum function) in past chapters. These are expressions that access a property of some value.

In the first case, we access the **length property** of the value in myString. In the second, we access the **property named max in the Math object** (which is a collection of mathematics-related constants and functions).

**NOTE:** Almost all JavaScript values have properties. The exceptions are null and undefined. If you try to access a property on one of these nonvalues, you get an error.

```
null.length;
// → TypeError: null has no properties
```

---

### Dot vs Bracket Notation/selecting (what is really happening!)

The two main ways to access properties in JavaScript are with a dot and with square brackets.

Both value.x and value[x] access a property on value—but not necessarily the same property. The difference is in how x is interpreted.

**NOTE:** When using a dot, the word after the dot is the literal name of the property.

**NOTE:** When using square brackets, the expression between the brackets is evaluated to get the property name.

Whereas value.x fetches the property of value named “x”, value[x] tries to evaluate the expression x and uses the result, converted to a string, as the property name.

So if you know that the property you are interested in is called color, you say value.color. If you want to extract the property named by the value held in the binding i, you say value[i].

Property names are strings. They can be any string, but the dot notation works only with names that look like valid binding names.

So if you want to access a property named 2 or John Doe, you must use square brackets: value[2] or value["John Doe"].

Because you can’t use the dot notation with numbers and usually want to use a binding that holds the index anyway, you have to use the bracket notation to get at them.

The length property of an array tells us how many elements it has. This property name is a valid binding name, and we know its name in advance, so to find the length of an array, you typically write array.length because that’s easier to write than array["length"].

---

### Methods

Properties that contain functions are generally called methods of the value they belong to, as in “toUpperCase is a method of a string”.

The push method adds values to the end of an array, and the pop method does the opposite, removing the last value in the array and returning it.

These somewhat silly names are the traditional terms for operations on a stack. A stack, in programming, is a data structure that allows you to push values into it and pop them out again in the opposite order so that the thing that was added last is removed first.

---

### Difference between Object.keys and Object.assign

To find out what properties an object has, you can use the Object.keys function. You give it an object, and it returns an array of strings—the object’s property names.

```
console.log(Object.keys({x: 0, y: 0, z: 2}));
// → ["x", "y", "z"]
```

There’s an Object.assign function that copies all properties from one object into another.

```
let objectA = {a: 1, b: 2};
Object.assign(objectA, {b: 3, c: 4});
console.log(objectA);
// → {a: 1, b: 3, c: 4}
```

#### Mutability
