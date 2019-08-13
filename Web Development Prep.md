## Javascript Promises
One of the most commonly asked questions around Javascript is about Promises. Be prepared to write some code around promises in an interview. It’s also a good skill to have! You probably want to review the following subjects:

### What is a promise?
An _asynchronous operation_ is one that allows the computer to “move on” to other tasks while waiting for the asynchronous operation to complete.

Web development makes use of _asynchronous operations_. Operations like making a network request or querying a database can be time-consuming, but JavaScript allows us to execute other tasks while awaiting their completion. Modern JavaScript handles asynchronicity using the `Promise` object, introduced with _ES6_. 

* Promises are JavaScript objects that represent the eventual result of an asynchronous operation.
* Promises can be in one of three states: 
  * **pending**: The initial state— the operation has not completed yet.
  * **resolved**: The operation has completed successfully and the promise now has a resolved value. For example, a request’s promise might resolve with a JSON object as its value.
  * **rejected**: The operation has failed and the promise has a reason for the failure. This reason is usually an `Error` of some kind.
* A promise is **settled** if it is either _resolved_ or _rejected_. Once settled, a promise can not be resettled. Calling `resolve()` or `reject()` again will have no effect. The immutability of a settled promise is an important feature.
* We construct a promise by using the `new` keyword and passing an `executor function` to the Promise constructor method.
* `setTimeout()` is a Node function which delays the execution of a callback function using the event-loop. `setTimeout()` has two parameters: a _callback_ function and a _delay_ in milliseconds.
* We use `.then()` with a _success handler callback_ containing the logic for what should happen if a promise resolves.
* We use `.catch()` with a _failure handler callback_ containing the logic for what should happen if a promise rejects.
* Promise composition enables us to write complex, asynchronous code that’s still readable. We do this by chaining multiple `.then()`‘s and `.catch()`‘s.
* To use promise composition correctly, we have to remember to return promises constructed within a `.then()`.
* We should `chain` multiple promises rather than nesting them.
* To take advantage of concurrency, we can use `Promise.all()`.

### How do you write your own promise?
* To create a new `Promise` object, we use the `new` keyword and the `Promise` constructor method:
  ```
  const executorFunction = (resolve, reject) => { };
  const myFirstPromise = new Promise(executorFunction);
  ```
* The `Promise` constructor method takes a function parameter called the `executor function` which runs automatically when the constructor is called. The _executor function_ generally starts an asynchronous operation and dictates how the promise should be settled.
* The _executor function_ has two function parameters, usually referred to as the `resolve()` and `reject()` functions. The `resolve()` and `reject()` functions _aren’t defined by the programmer_. When the Promise constructor runs, JavaScript will pass its own `resolve()` and `reject()` functions into the _executor function_.
  * `resolve` is a function with one argument. Under the hood, if invoked, `resolve()` will change the promise’s status from _pending_ to _fulfilled_, and the promise’s resolved value will be set to the argument passed into `resolve()`.
  * `reject` is a function that takes a reason or error as an argument. Under the hood, if invoked, `reject()` will change the promise’s status from _pending_ to _rejected_, and the promise’s rejection reason will be set to the argument passed into `reject()`.
  
```
const inventory = {
  sunglasses: 10,
  pants: 1088,
  bags: 1344
};

// Executor function:
const myExecutor = (resolve, reject) => {
  if (inventory.sunglasses) {
    resolve('Sunglasses order processed.');
  } else {
    reject('That item is sold out.');
  }
};

const orderSunglassesPromise = new Promise(myExecutor);

orderSunglassesPromise
  .then(result => console.log(result))
  .catch(err => console.log(err);

```
In our example, `myFirstPromise` resolves or rejects based on a simple condition, but, in practice, promises settle based on the results of asynchronous operations. For example, a database request may fulfill with the data from a query or reject with an error thrown. 

### How do you get the result of a promise (ex. from an API call)?
### How do you get the result from multiple promises in order (using Promise.all, etc.)?
