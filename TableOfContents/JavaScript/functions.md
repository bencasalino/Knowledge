### forEach()

There is a built-in array method, forEach, that provides something like a for/of loop as a higher-order function.

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
