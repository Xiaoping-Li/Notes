## Javascript Promises
One of the most commonly asked questions around Javascript is about Promises. Be prepared to write some code around promises in an interview. It’s also a good skill to have! You probably
want to review the following subjects:

### What is a promise?
* Promises are JavaScript objects that represent the eventual result of an asynchronous operation.
* Promises can be in one of three states: **pending, resolved**, or **rejected**.
* A promise is **settled** if it is either _resolved_ or _rejected_. Once settled, a promise can not be resettled. Calling `resolve()` or `reject()` again will have no effect. The immutability of a settled promise is an important feature.
* We construct a promise by using the `new` keyword and passing an `executor function` to the Promise constructor method.
* `setTimeout()` is a Node function which delays the execution of a callback function using the event-loop.
* We use `.then()` with a _success handler callback_ containing the logic for what should happen if a promise resolves.
* We use `.catch()` with a _failure handler callback_ containing the logic for what should happen if a promise rejects.
* Promise composition enables us to write complex, asynchronous code that’s still readable. We do this by chaining multiple `.then()`‘s and `.catch()`‘s.
* To use promise composition correctly, we have to remember to return promises constructed within a `.then()`.
* We should `chain` multiple promises rather than nesting them.
* To take advantage of concurrency, we can use `Promise.all()`.



### How do you write your own promise?
### How do you get the result of a promise (ex. from an API call)?
### How do you get the result from multiple promises in order (using Promise.all, etc.)?

