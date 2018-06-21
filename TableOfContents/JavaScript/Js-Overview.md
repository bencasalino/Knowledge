Reserved Keywords

- break
- default
- function
- return
- var
- case
- delete
- if
- switch
- void
- catch
- do
- in
- this
- while
- const
- else
- instanceof
- throw
- with
- continue
- finally
- let
- try
- debugger
- for
- new
- typeof

[Future Reserved Words](https://docs.microsoft.com/en-us/scripting/javascript/reference/javascript-future-reserved-words)

---

#Unicode and UTF-16
JavaScript strings are encoded as a sequence of 16-bit numbers. These are called code units. A Unicode character code was initially supposed to fit within such a unit (which gives you a little over 65,000 characters). When it became clear that wasn’t going to be enough, many people balked at the need to use more memory per character. To address these concerns, UTF-16, the format used by JavaScript strings, was invented. It describes most common characters using a single 16-bit code unit but uses a pair of two such units for others.

UTF-16 is generally considered a bad idea today. It seems almost intentionally designed to invite mistakes. It’s easy to write programs that pretend code units and characters are the same thing. And if your language doesn’t use two-unit characters, that will appear to work just fine. But as soon as someone tries to use such a program with some less common Chinese characters, it breaks. Fortunately, with the advent of emoji, everybody has started using two-unit characters, and the burden of dealing with such problems is more fairly distributed.

Unfortunately, obvious operations on JavaScript strings, such as getting their length through the length property and accessing their content using square brackets, deal only with code units.

```
// Two emoji characters, horse and shoe
let horseShoe = "🐴👟";
console.log(horseShoe.length);
// → 4

console.log(horseShoe[0]);
// → (Invalid half-character)

console.log(horseShoe.charCodeAt(0));
// → 55357 (Code of the half-character)

console.log(horseShoe.codePointAt(0));
// → 128052 (Actual code for horse emoji)
```

---

# charCodeAt and codePointAt

JavaScript’s **charCodeAt** method gives you a code unit, not a full character code. The **codePointAt** method, added later, does give a full Unicode character.

A for/of loop can also be used on strings. Like codePointAt, this type of loop was introduced at a time where people were acutely aware of the problems with UTF-16. When you use it to loop over a string, it gives you real characters, not code units.

```
let roseDragon = "🌹🐉";
for (let char of roseDragon) {
  console.log(char);
}
// → 🌹
// → 🐉
```

---

Example:

```
a = b * 2;
```

- 2 is a **literal value expression**
- b is a **variable expression**, which means to retrieve its current value.
- b \* 2 is an **arithmetic expression**, which means to do the multiplication.
- a = b _ 2 is an **assignment expression**, which means to assign the result of the b _ 2 expression to the variable.

Statement

> a group of words, numbers and operators that preform a specific task.

Variables

> simple boxes/containers to store things in.

Literal Value

> Ex: the 2 value itself, called a literal value, because it stands alone without being stored in a variable.

Operators

> they preform actions with the values and variables such as assignment and mathematic multiplication.

Expressions

> Statements are made up of one or more expressions.

Call Expression

> when the entire statement is the function call expression itself. ex: alert ("hi");

---

Interpreter and Compiler

> Special utility that is used to translate the code into commands that the computer can understand.

Compiler

> For some languages, the translation is done ahead of time, called compiling the code. So when the program runs later, whats running is actually compiled computer instructions ready to go.

Interpreter

> JS is an interpreter language, because your JS source code is processed each time it's run. But technically the JS engine actually compiles the program on the fly then immediately runs he complied code.

---

## Question: Similar to pre-processing like **SASS** or transpile the code like **Babel**?

#Operators

Assignment

> =, as in a = 2

Math

Compound Assignment

> a += 2 is the same as a = a + 2

Increment/Decrement

Equality

Comparison

Logical

Object Property Access

> . --> as in console . log()

**NOTE:** Objects are values that hold other calues at specific named locations called **properties**.

**obj.a** --> means the object value called obj with a property name of a. Properties can alternatively be accessed as **obj["a"]**

---

### Values and Types

Types

>

Primitives

>

Literals

>

---

#### Type conversion/coercion & implicit/explicit

Loosely Typed vs Strong Typed Languages

Dynamic Typing / Weak Typing / Static Typing

Type Enforcement

---
