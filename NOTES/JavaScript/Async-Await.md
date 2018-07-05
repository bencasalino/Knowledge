#### Async/Await

Promise, try catch, finally

This, by far, is the most important and most useful feature if you ask me. Async functions allows us to not deal with callback hell and make the entire code look simple.

The async keyword tells the JavaScript compiler to treat the function differently. The compiler pauses whenever it reaches the await keyword within that function. It assumes that the expression after await returns a promise and waits until the promise is resolved or rejected before moving further.

Promise.prototype.finally()
finally() is a new instance method that was added to Promise. The main idea is to allow running a callback after either resolve or reject to help clean things up. The finally callback is called without any value and is always executed no matter what.
