## First-Class Functions / Higher Order Functions / Native Array Methods

Functions that operate on other functions, either by taking them as arguments or by returning them, are called higher-order functions. The term comes from mathematics, where the distinction between functions and other values is taken more seriously.

Higher-order functions allow us to abstract over **actions**, not just values. Higher-order functions start to shine when you need to compose operations.

A programming language is said to have First Class Functions when a function in that language are treated like any other variable.

A function can be...

> passed as an argument to another function
> can be returned by another function
> can be assigned as a value to a variable

Being able to pass function values to other functions is a deeply useful aspect of JavaScript. It allows us to write functions that model computations with “gaps” in them. The code that calls these functions can fill in the gaps by providing function values.

Arrays provide a number of useful higher-order methods.

You can use **forEach** to loop over the elements in an array.

The **filter** method returns a new array containing only the elements that pass the predicate function.

Transforming an array by putting each element through a function is done with **map**.

You can use **reduce** to combine all the elements in an array into a single value.

The **some** method tests whether any element matches a given predicate function.

And **findIndex** finds the position of the first element that matches a predicate.

---

#Filter

Filtering arrays

To find the scripts in the data set that are still in use, the following function might be helpful. It filters out the elements in an array that don’t pass a test.

### Use cases for filter

- returns a new array that only includes things that PASS our "test"
- checks every item/index in an array against a condition.
- new array will be of EQUAL or LESSER length than the input.

```
function filter(array, test) {
  let passed = [];
  for (let element of array) {
    if (test(element)) {
      passed.push(element);
    }
  }
  return passed;
}
```

The function uses the argument named test, a function value, to fill a “gap” in the computation—the process of deciding which elements to collect.

Note how the filter function, rather than deleting elements from the existing array, builds up a new array with only the elements that pass the test. This function is **pure**.

**NOTE:** It does not modify the array it is given.

Like forEach, filter is a standard array method. The example defined in the function only to show what it does internally. It does not return a new array it just replaces or updates the current array. For each eseentially replaces the for loop with different syntax.

---

#Map

The map method transforms an array by applying a function to all of its elements and building a new array from the returned values.

The new array will have the same length as the input array, but its content will have been mapped to a new form by the function.

### Use cases for map:

- Takes an array of data and transform each index in the same way
- When using push, pop etc. it modifies the current array, when using map it returns a **new** array.
- often used to reformat or clean up data
- ALWAYS returns an array of the same length.
- MUST include a return statement.

```
function map(array, transform) {
  let mapped = [];
  for (let element of array) {
    mapped.push(transform(element));
  }
  return mapped;
}
```

Example:

```
// define the data
const numberArray = [2, 4, 5];

// define the function that will be mapped
const doubleArray = numberArray.map(double);

// this is what map will do
function double(number) {
  return number * 2;
}

//display results
console.log(doubleArray);
```

---

#Reduce

Another common thing to do with arrays is to compute a single value from them. Our recurring example, summing a collection of numbers, is an instance of this. Another example is finding the script with the most characters.

The higher-order operation that represents this pattern is called reduce (sometimes also called **fold**). It builds a value by repeatedly taking a single element from the array and combining it with the current value. When summing numbers, you’d start with the number zero and, for each element, add that to the sum.

The parameters to reduce are, apart from the array, a combining function and a start value. This function is a little less straightforward than filter and map.

The standard array method reduce, which of course corresponds to this function, has an added convenience. If your array contains at least one element, you are allowed to leave off the start argument. The method will take the first element of the array as its start value and start reducing at the second element.

### Use cases for reduce:

- takes all items in an array and reduces to a single value.
- swiss army knife of native array methods.
- you could essential run a map or filter with the reduce native array method
- could not necessarily return a new array, could be object, string, number etc.

```
function reduce(array, combine, start) {
  let current = start;
  for (let element of array) {
    current = combine(current, element);
  }
  return current;
}

console.log(reduce([1, 2, 3, 4], (a, b) => a + b, 0));
// → 10
```

#Some
The some method is another higher-order function. It takes a test function and tells you whether that function returns true for any of the elements in the array.

#Every
Analogous to the some method, arrays also have an every method. This one returns true when the given function returns true for every element in the array. In a way, some is a version of the || operator that acts on arrays, and every is like the && operator.
