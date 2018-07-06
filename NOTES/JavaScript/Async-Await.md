#### Async/Await

Promise, try catch, finally

This, by far, is the most important and most useful feature if you ask me. Async functions allows us to not deal with callback hell and make the entire code look simple.

The async keyword tells the JavaScript compiler to treat the function differently. The compiler pauses whenever it reaches the await keyword within that function. It assumes that the expression after await returns a promise and waits until the promise is resolved or rejected before moving further.

Promise.prototype.finally()
finally() is a new instance method that was added to Promise. The main idea is to allow running a callback after either resolve or reject to help clean things up. The finally callback is called without any value and is always executed no matter what.

---

A Promise is in one of these states:

pending: initial state, neither fulfilled nor rejected.

fulfilled: meaning that the operation completed successfully.

rejected: meaning that the operation failed.

A pending promise can either be fulfilled with a value, or rejected with a reason (error). When either of these options happens, the associated handlers queued up by a promise's then method are called.

---

Synchronous means each operation must wait for the previous one to complete.

Asynchronous means an operation can occur while another operation is still being processed.

In JavaScript, all code is synchronous due to the single-threaded nature of it. However, asynchronous operations not part of the program (such as XMLHttpRequest or setTimeout) are processed outside of the main thread because they are controlled by native code (browser APIs), but callbacks part of the program will still be executed synchronously.

---
