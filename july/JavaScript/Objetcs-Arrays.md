###### Summary:

Objects and arrays (which are a specific kind of object) provide ways to group several values into a single value. Conceptually, this allows us to put a bunch of related things in a bag and run around with the bag, instead of wrapping our arms around all of the individual things and trying to hold on to them separately.

Most values in JavaScript have properties, the exceptions being **null and undefined**.

Properties are accessed using value.prop or value["prop"].

**Objects** tend to use names for their properties and store more or less a fixed set of them.

**Arrays**, on the other hand, usually contain varying amounts of conceptually identical values and use numbers (starting from 0) as the names of their **properties**.

There are some named **properties** in arrays, such as **length** and a number of methods.

**Methods** are functions that live in properties and (usually) act on the value they are a **property** of.

You can iterate over arrays using a special kind of for loop—for (let element of array).

---

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

---

#### Mutability

We saw that object values can be modified. The types of values discussed in earlier chapters, such as numbers, strings, and Booleans, are all **immutable**, it is impossible to change values of those types. You can combine them and derive new values from them, but when you take a specific string value, that value will always remain the same.

The text inside it **CANNOT** be changed. If you have a string that contains "cat", it is not possible for other code to change a character in your string to make it spell "rat".

Objects work differently. You **CAN** change their properties, causing a single object value to have different content at different times.

Values of type string, number, and Boolean are not objects, and though the language doesn’t complain if you try to set new properties on them, it doesn’t actually store those properties. As mentioned earlier, such values are immutable and cannot be changed.

When we have two numbers, 120 and 120, we can consider them precisely the same number, whether or not they refer to the same physical bits. With objects, there is a difference between having two references to the same object and having two different objects that contain the same properties.

```
let object1 = {value: 10};
let object2 = object1;
let object3 = {value: 10};

console.log(object1 == object2);
// → true
console.log(object1 == object3);
// → false

object1.value = 15;
console.log(object2.value);
// → 15
console.log(object3.value);
// → 10
```

The object1 and object2 bindings grasp the same object, which is why changing object1 also changes the value of object2. They are said to have the same identity. The binding object3 points to a different object, which initially contains the same properties as object1 but lives a separate life.

????

```
let journal = [];

function addEntry(events, squirrel) {
  journal.push({events, squirrel});
}
```

Note that the object added to the journal looks a little odd. Instead of declaring properties like events: events, it just gives a property name. This is shorthand that means the same thing—if a property name in brace notation isn’t followed by a value, its value is taken from the binding with the same name.

```
addEntry(["work", "touched tree", "pizza", "running",
          "television"], false);
addEntry(["work", "ice cream", "cauliflower", "lasagna",
          "touched tree", "brushed teeth"], false);
addEntry(["weekend", "cycling", "break", "peanuts",
          "beer"], true);
```

---

##### indexOf & lastindexOf method?

Both indexOf and lastIndexOf take an optional second argument that indicates where to start searching.

```
console.log([1, 2, 3, 2, 1].indexOf(2));
// → 1
console.log([1, 2, 3, 2, 1].lastIndexOf(2));
// → 3
```

---

##### .concat method?

The concat method can be used to glue arrays together to create a new array, similar to what the + operator does for strings. The following example shows both concat and slice in action. It takes an array and an index, and it returns a new array that is a copy of the original array with the element at the given index removed.

```
function remove(array, index) {
  return array.slice(0, index)
    .concat(array.slice(index + 1));
}
console.log(remove(["a", "b", "c", "d", "e"], 2));
// → ["a", "b", "d", "e"]
```

**NOTE:** If you pass concat an argument that is not an array, that value will be added to the new array as if it were a one-element array.

---

#### .split and .join

You can split a string on every occurrence of another string with split and join it again with join.

```
let sentence = "Secretarybirds specialize in stomping";
let words = sentence.split(" ");
console.log(words);
// → ["Secretarybirds", "specialize", "in", "stomping"]
console.log(words.join(". "));
// → Secretarybirds. specialize. in. stomping
```

---

### Rest parameters and Spread Operator

Rest:

It can be useful for a function to accept any number of arguments. For example, Math.max computes the maximum of all the arguments it is given.

To write such a function, you put three dots before the function’s last parameter, like this:

```
function max(...numbers) {
  let result = -Infinity;
  for (let number of numbers) {
    if (number > result) result = number;
  }
  return result;
}
console.log(max(4, 1, 9, -2));
// → 9
```

When such a function is called, the rest parameter is bound to an array containing all further arguments. If there are other parameters before it, their values aren’t part of that array. When, as in max, it is the only parameter, it will hold all arguments.

Spread:

You can use a similar three-dot notation to call a function with an array of arguments.

```
let numbers = [5, 1, 7];
console.log(max(...numbers));
// → 7
```

This “spreads” out the array into the function call, passing its elements as separate arguments. It is possible to include an array like that along with other arguments, as in max(9, ...numbers, 2).

Square bracket array notation similarly allows the triple-dot operator to spread another array into the new array.

```
let words = ["never", "fully"];
console.log(["will", ...words, "understand"]);
// → ["will", "never", "fully", "understand"]
```

### Math Object

The Math object is used as a container to group a bunch of related functionality. There is only one Math object, and it is almost never useful as a value. Rather, it provides a **namespace** so that all these functions and values do not have to be global bindings.

Having too many global bindings “pollutes” the **namespace**. The more names have been taken, the more likely you are to accidentally overwrite the value of some existing binding.

For example, it’s not unlikely to want to name something max in one of your programs. Since JavaScript’s built-in max function is tucked safely inside the Math object, we don’t have to worry about overwriting it.

Many languages will stop you, or at least warn you, when you are defining a binding with a name that is already taken. JavaScript does this for bindings you declared with let or const but—perversely—not for standard bindings nor for bindings declared with var or function.

Common:

```
Math.floor()
Math.ceil()
Math.round()
Math.min()
Math.max()
Math.random()
```

Less Common:

```
Math.sqrt()
Math.PI()
Math.cos,sine,tan etc.
```

---
