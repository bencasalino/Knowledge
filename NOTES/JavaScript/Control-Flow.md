Scope / Blocks / Hoisting / Closures

var/let/const

**NOTE:** By convention, JS variables as constants are usually capitalized, with underscores \_ between multiple words.

> var TAX_RATE = 0.08; //8% sales tax

### Blocks

Code we often need to group into a serries of statements together is often called a **block**.
Unlike most statements a block does not need a semi-colon after it.

### Closure

Closure is one of the most important, and often least understood, concepts in JavaScript. I won't cover it in deep detail here, and instead refer you to the Scope & Closures title of this series. But I want to say a few things about it so you understand the general concept. It will be one of the most important techniques in your JS skillset.

You can think of closure as a way to "remember" and continue to access a function's scope (its variables) even once the function has finished running.

Consider:

```
function makeAdder(x) {
	// parameter `x` is an inner variable

	// inner function `add()` uses `x`, so
	// it has a "closure" over it
	function add(y) {
		return y + x;
	};

	return add;
}
```

The reference to the inner add(..) function that gets returned with each call to the outer makeAdder(..) is able to remember whatever x value was passed in to makeAdder(..). Now, let's use makeAdder(..):

---

### Modules

The most common usage of closure in JavaScript is the module pattern. Modules let you define private implementation details (variables, functions) that are hidden from the outside world, as well as a public API that is accessible from the outside.

Consider:

```
function User(){
	var username, password;

	function doLogin(user,pw) {
		username = user;
		password = pw;

		// do the rest of the login work
	}

	var publicAPI = {
		login: doLogin
	};

	return publicAPI;
}

// create a `User` module instance
var fred = User();

fred.login( "fred", "12Battery34!" );
```

---

Explanation:

The User() function serves as an outer scope that holds the variables username and password, as well as the inner doLogin() function; these are all private inner details of this User module that cannot be accessed from the outside world.

Warning: We are not calling new User() here, on purpose, despite the fact that probably seems more common to most readers. User() is just a function, not a class to be instantiated, so it's just called normally. Using new would be inappropriate and actually waste resources.

Executing User() creates an instance of the User module -- a whole new scope is created, and thus a whole new copy of each of these inner variables/functions. We assign this instance to fred. If we run User() again, we'd get a new instance entirely separate from fred.

The inner doLogin() function has a closure over username and password, meaning it will retain its access to them even after the User() function finishes running.

publicAPI is an object with one property/method on it, login, which is a reference to the inner doLogin() function. When we return publicAPI from User(), it becomes the instance we call fred.

At this point, the outer User() function has finished executing. Normally, you'd think the inner variables like username and password have gone away. But here they have not, because there's a closure in the login() function keeping them alive.

That's why we can call fred.login(..) -- the same as calling the inner doLogin(..) -- and it can still access username and password inner variables.

---

# this (Identifier)

While it may often seem that this is related to "object-oriented patterns," in JS this is a different mechanism.

If a function has a this reference inside it, that this reference usually points to an object. But which object it points to depends on how the function was called.

It's important to realize that this does not refer to the function itself, as is the most common misconception.

Bottom line: to understand what this points to, you have to examine how the function in question was called. It will be one of those four ways just shown, and that will then answer what this is.

---

#Prototypes

When you reference a property on an object, if that property doesn't exist, JavaScript will automatically use that object's internal prototype reference to find another object to look for the property on. You could think of this almost as a fallback if the property is missing.

---

###Polyfilling
The word "polyfill" is an invented term (by Remy Sharp) (https://remysharp.com/2010/10/08/what-is-a-polyfill) used to refer to taking the definition of a newer feature and producing a piece of code that's equivalent to the behavior, but is able to run in older JS environments.

---

#Transpiling

So the better option is to use a tool that converts your newer code into older code equivalents. This process is commonly called "transpiling," a term for transforming + compiling.

There are several important reasons you should care about transpiling:

The new syntax added to the language is designed to make your code more readable and maintainable. The older equivalents are often much more convoluted. You should prefer writing newer and cleaner syntax, not only for yourself but for all other members of the development team.
If you transpile only for older browsers, but serve the new syntax to the newest browsers, you get to take advantage of browser performance optimizations with the new syntax. This also lets browser makers have more real-world code to test their implementations and optimizations on.
Using the new syntax earlier allows it to be tested more robustly in the real world, which provides earlier feedback to the JavaScript committee (TC39). If issues are found early enough, they can be changed/fixed before those language design mistakes become permanent.

---

Tokenizing/Lexing: breaking up a string of characters into meaningful (to the language) chunks, called tokens. For instance, consider the program: var a = 2;. This program would likely be broken up into the following tokens: var, a, =, 2, and ;. Whitespace may or may not be persisted as a token, depending on whether it's meaningful or not.
