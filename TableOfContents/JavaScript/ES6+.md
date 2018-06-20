Resources:

# ES6+

[ES Examples](https://medium.freecodecamp.org/here-are-examples-of-everything-new-in-ecmascript-2016-2017-and-2018-d52fa3b5a70e)

#### Array.prototype.includes

"includes" is a simple instance method on the Array and helps to easily find if an item is in the Array (including NaN unlike indexOf)

```
const arr = [1,2,3]

// instead of using indexOf
if (arr.indexOf(2) >= 0) {
  console.log(true);
};

//Use
if(arr.includes(2)) {
};
```

## console.log(true);

#### Exponent "infix" operator

```
// instead of
Math.pow(7,2) // 49

// Use
7**2 // 49
```

---

#### Object.values()

Is a new function that is similar to Object.keys() but returns all the values of the Object's own properties excluding any value(s) in the prototypical chain.

```
const cars = {BMC: 31, Tesla: 88};

//ES2015 instead of...
const vals = Object.keys(cars).map(key => cars][key]);  // [31, 88]

//ES2017 use...
const values = Object.values(cars);
console.log(values); // [31, 88]
```

---

#### Object.entries()

Object.entries() is related to Object.keys, but instead of returning just keys, it returns both keys and values in the array fashion. This makes it simple to do thinks like using objects in loops or converting objects into Maps.

```
const map = new Map(Object.entries(cars));

console.log(map);
// Map {'BMW' => 3, 'Tesla' => 42}
```

---

#### String padding

Two instance methods were added to String — String.prototype.padStart and String.prototype.padEnd — that allow appending/prepending either an empty string or some other string to the start or the end of the original string.

---

#### Object.getOwnPropertyDescriptors

This method returns all the details (including getter get and setter set methods) for all the properties of a given object.

The main motivation to add this is to allow shallow copying / cloning an object into another object that also copies getter and setter functions as opposed to Object.assign .

---

Rest operator vs Spread operator
Spread properties also look just like rest properties with three dots ... but the difference is that you use spread to create (restructure) new objects.
