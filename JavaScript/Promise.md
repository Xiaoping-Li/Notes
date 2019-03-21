# Promise
**Promises** are objects that represent the eventual outcome of an asynchronous operation. A `Promise` object can be in one of three states:

* **Pending**: The initial state— the operation has not completed yet.
* **Fulfilled**: The operation has completed successfully and the promise now has a resolved value. For example, a request’s promise might resolve with a JSON object as its value.
* **Rejected**: The operation has failed and the promise has a reason for the failure. This reason is usually an Error of some kind.

## Constructing a Promise Object
To create a new `Promise` object, we use the `new` keyword and the `Promise` constructor method:
```
const executorFunction = (resolve, reject) => { };
const myFirstPromise = new Promise(executorFunction);
```

The `Promise` constructor method takes a function parameter called the _executor function_ which runs automatically when the constructor is called. The executor function generally starts an asynchronous operation and dictates how the promise should be settled.

The _executor function_ has two function parameters, usually referred to as the `resolve()` and `reject()` functions. The `resolve()` and `reject()` functions aren’t defined by the programmer. When the `Promise` constructor runs, JavaScript will pass **its own** `resolve()` and `reject()` functions into the executor function.

* **resolve** is a function with one argument. Under the hood, if invoked, `resolve()` will change the promise’s status from **pending** to **fulfilled**, and the promise’s resolved value will be set to the argument passed into `resolve()`.
* **reject** is a function that takes a _reason or error_ as an argument. Under the hood, if invoked, `reject()` will change the promise’s status from **pending** to **rejected**, and the promise’s rejection reason will be set to the argument passed into `reject()`.

In practice, promises settle based on the results of asynchronous operations. For example, a database request may fulfill with the data from a query or reject with an error thrown.
