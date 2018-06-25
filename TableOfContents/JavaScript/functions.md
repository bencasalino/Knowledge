### forEach()

There is a built-in array method, forEach, that provides something like a for/of loop as a higher-order function.

Like forEach, filter is a standard array method. The example defined in the function only to show what it does internally. It does not return a new array it just replaces or updates the current array. For each eseentially replaces the for loop with different syntax.

```
["A", "B"].forEach(l => console.log(l));
// → A
// → B
```

---

Abstractions

> In the context of programming, these kinds of vocabularies are usually called abstractions. Abstractions hide details and give us the ability to talk about problems at a higher (or more abstract) level.

---

Function that creates a new functions:
(still a little confusing)

```
function greaterThan(n) {
  return m => m > n;
}
let greaterThan10 = greaterThan(10);
console.log(greaterThan10(11));
// → true
```

### Functions as Values

```
function foo() {
	// ..
}
```

Though it may not seem obvious from that syntax, foo is basically just a variable in the outer enclosing scope that's given a reference to the function being declared. That is, the function itself is a value, just like 42 or [1,2,3] would be.

This may sound like a strange concept at first, so take a moment to ponder it. Not only can you pass a value (argument) to a function, but a function itself can be a value that's assigned to variables, or passed to or returned from other functions.

As such, a function value should be thought of as an expression, much like any other value or expression.

Consider:

```
var foo = function() {
	// ..
};

var x = function bar(){
	// ..
};
```

The first function expression assigned to the foo variable is called anonymous because it has no name.

The second function expression is named (bar), even as a reference to it is also assigned to the x variable. Named function expressions are generally more preferable, though anonymous function expressions are still extremely common.

---

### Immediately Invoked Function Expressions (IIFEs)

In the previous snippet, neither of the function expressions are executed -- we could if we had included foo() or x(), for instance.

There's another way to execute a function expression, which is typically referred to as an immediately invoked function expression (IIFE):

```
(function IIFE(){
	console.log( "Hello!" );
})();
// "Hello!"
```

The outer ( .. ) that surrounds the (function IIFE(){ .. }) function expression is just a nuance of JS grammar needed to prevent it from being treated as a normal function declaration.

The final () on the end of the expression -- the })(); line -- is what actually executes the function expression referenced immediately before it.

That may seem strange, but it's not as foreign as first glance. Consider the similarities between foo and IIFE here:

```
function foo() { .. }

// `foo` function reference expression,
// then `()` executes it
foo();

// `IIFE` function expression,
// then `()` executes it
(function IIFE(){ .. })();
```

As you can see, listing the (function IIFE(){ .. }) before its executing () is essentially the same as including foo before its executing (); in both cases, the function reference is executed with () immediately after it.
