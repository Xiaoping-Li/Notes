## Javascript Promises
One of the most commonly asked questions around Javascript is about Promises. Be prepared to write some code around promises in an interview. It’s also a good skill to have! You probably want to review the following subjects:

### What is a promise (ES6)?
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
```
In our example, `myFirstPromise` resolves or rejects based on a simple condition, but, in practice, promises settle based on the results of asynchronous operations. For example, a database request may fulfill with the data from a query or reject with an error thrown. 

### How do you get the result of a promise (ex. from an API call)?
```
orderSunglassesPromise
  .then(result => console.log(result))
  .catch(err => console.log(err);
```
* `.then()` is a higher-order function — it takes two callback functions as arguments. We refer to these callbacks as _handlers_. When the promise settles, the appropriate _handler_ will be invoked with that settled value. 
 * The first handler, `onFulfilled`, is a _success handler_, and it should contain the logic for the promise resolving.
 * The second handler, `onRejected`, is a _failure handler_, and it should contain the logic for the promise rejecting.
 
 **Note**: We can invoke `.then()` with one, both, or neither handler! This allows for flexibility, but it can also make for tricky debugging. One important feature of `.then()` is that it always returns a promise. `.then()` will return a promise with the same settled value as the promise it was called on if no appropriate handler was provided. This implementation allows us to separate our _resolved logic_ from our _rejected logic_.

* The `.catch()` function takes only one argument, `onRejected`. In the case of a rejected promise, this failure handler will be invoked with the reason for rejection. 
 ```
 prom
  .then((resolvedValue) => {
    console.log(resolvedValue);
  })
  .catch((rejectionReason) => {
    console.log(rejectionReason);
  });
  ```
 **Note**: If the promise rejects, `.then()` will return a promise with the same rejection reason as the original promise and `.catch()`‘s failure handler will be invoked with that rejection reason.

### How do you get the result from multiple promises in order (using Promise.all, etc.)?
`Promise.all()` accepts an array of promises as its argument and returns a single promise. That single promise will settle in one of two ways:
* If _every_ promise in the argument array resolves, the single promise returned from `Promise.all()` will resolve with an array containing the resolve value from each promise in the argument array.
* If _any_ promise from the argument array rejects, the single promise returned from `Promise.all()` will immediately reject with the reason that promise rejected. This behavior is sometimes referred to as _failing fast_.

### async...await syntax (ES8)
Often in web development, we need to handle asynchronous actions— actions we can wait on while moving on to other tasks. We make requests to networks, databases, or any number of similar operations. JavaScript is non-blocking: instead of stopping the execution of code while it waits, JavaScript uses an `event-loop` which allows it to efficiently execute other tasks while it awaits the completion of these asynchronous actions.
* The `async` keyword is used to write functions that handle asynchronous actions. We wrap our asynchronous logic inside a function prepended with the `async keyword`. Then, we invoke that function.
```
async function myFunc() {};
---------------------------
const myFunc = async () => {};

myFunc();
```
 * `async` functions always return a promise. This means we can use traditional promise syntax, like `.then()` and `.catch` with our async functions.
 * An async function will return in one of three ways:
  * If there’s nothing returned from the function, it will return a promise with a resolved value of undefined.
  * If there’s a non-promise value returned from the function, it will return a promise resolved to that value.
  * If a promise is returned from the function, it will simply return that promise
 ```
 async function fivePromise() { 
   return 5;
 }

 fivePromise()
 .then(resolvedValue => {
     console.log(resolvedValue);
   })  // Prints 5
  ```
* The `await` keyword can only be used inside an `async` function. `await` is an operator: it returns the resolved value of a promise. Since promises resolve in an _indeterminate_ amount of time, `await` halts, or pauses, the execution of our `async` function until a given promise is resolved.
* When `.catch()` is used with a long promise chain, there is no indication of where in the chain the error was thrown. This can make debugging challenging. With `async...await`, we use `try...catch` statements for error handling. 





