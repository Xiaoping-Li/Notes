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

## Consuming Promises
The initial state of an asynchronous promise is `pending`, but we have a guarantee that it will settle. How do we tell the computer what should happen then? Promise objects come with an aptly named `.then()` method. It allows us to say, “I have a promise, when it settles, **then** here’s what I want to happen…”

`.then()` is a higher-order function — it takes two callback functions as arguments. We refer to these callbacks as _handlers_. When the promise settles, the appropriate handler will be invoked with that settled value.

* The first handler, sometimes called `onFulfilled`, is a _success handler_, and it should contain the logic for the promise resolving.
* The second handler, sometimes called `onRejected`, is a _failure handler_, and it should contain the logic for the promise rejecting.

We can invoke `.then()` with one, both, or neither handler! This allows for flexibility, but it can also make for tricky debugging. If the appropriate handler is not provided, instead of throwing an error, `.then()` will just return a promise with the same settled value as the promise it was called on. One important feature of `.then()` is that it always returns a promise. 

## Using catch() with Promises
One way to write cleaner code is to follow a principle called _separation of concerns_. Separation of concerns means organizing code into distinct sections each handling a specific task. It enables us to quickly navigate our code and know where to look if something isn’t working.

The `.catch()` function takes only one argument, `onRejected`. In the case of a rejected promise, this failure handler will be invoked with the reason for rejection. Using `.catch()` accomplishes the same thing as using a `.then()` with only a failure handler.
```
prom
  .then((resolvedValue) => {
    console.log(resolvedValue);
  })
  .catch((rejectionReason) => {
    console.log(rejectionReason);
  });
```
  
 ## Chaining Multiple Promises
One common pattern we’ll see with asynchronous programming is multiple operations which depend on each other to execute or that must be executed in a certain order. We might make one request to a database and use the data returned to us to make another request and so on!

This process of chaining promises together is called _composition_. Promises are designed with composition in mind! Here’s a simple promise chain in code:
```
firstPromiseFunction()
.then((firstResolveVal) => {
  return secondPromiseFunction(firstResolveVal);
})
.then((secondResolveVal) => {
  console.log(secondResolveVal);
});
```

**Note**: In order for our chain to work properly, we had to **return** the promise `secondPromiseFunction(firstResolveVal)`. This ensured that the return value of the first `.then()` was our second promise rather than the default return of a new promise with the same settled value as the initial.

## Avoiding Common Mistakes
Promise composition allows for much more readable code than the nested callback syntax that preceded it. However, it can still be easy to make mistakes. In this exercise, we’ll go over two common mistakes with promise composition.

**Mistake 1**: Nesting promises instead of chaining them.
```
returnsFirstPromise()
.then((firstResolveVal) => {
  return returnsSecondValue(firstResolveVal)
    .then((secondResolveVal) => {
      console.log(secondResolveVal);
    })
})
```
Let’s break down what’s happening in the above code:

* We invoke `returnsFirstPromise()` which returns a promise.
* We invoke `.then()` with a success handler.
* Inside the success handler, we invoke `returnsSecondValue()` with firstResolveVal which will return a new promise.
* We invoke a second `.then()` to handle the logic for the second promise settling all inside the first `then()`!
* Inside that second `.then()`, we have a success handler which will log the second promise’s resolved value to the console.

Instead of having a clean chain of promises, we’ve nested the logic for one inside the logic of the other. Imagine if we were handling five or ten promises!

**Mistake 2**: Forgetting to return a promise.
```
returnsFirstPromise()
.then((firstResolveVal) => {
  returnsSecondValue(firstResolveVal)
})
.then((someVal) => {
  console.log(someVal);
})
```
Let’s break down what’s happening in the example:

* We invoke `returnsFirstPromise()` which returns a promise.
* We invoke `.then()` with a success handler.
* Inside the success handler, we create our second promise, but we forget to return it!
* We invoke a second `.then()`. It’s supposed to handle the logic for the second promise, but since we didn’t return, this `.then()` is invoked on a promise with the same settled value as the original promise!

Since forgetting to return our promise won’t throw an error, this can be a really tricky thing to debug!

## Using Promise.all()
When done correctly, promise composition is a great way to handle situations where asynchronous operations depend on each other or execution order matters. What if we’re dealing with multiple promises, we need **all** of these tasks to complete but not in any particular order? 

To maximize efficiency we should use _concurrency_, multiple asynchronous operations happening together. With promises, we can do this with the function `Promise.all()`.

`Promise.all()` accepts an array of promises as its argument and returns a single promise. That single promise will settle in one of two ways:

* If every promise in the argument array _resolves_, the single promise returned from `Promise.all()` will resolve with an array containing the resolve value from each promise in the argument array.
* If any promise from the argument array _rejects_, the single promise returned from `Promise.all()` will immediately reject with the reason that promise rejected. This behavior is sometimes referred to as _failing fast_.

```
let myPromises = Promise.all([returnsPromOne(), returnsPromTwo(), returnsPromThree()]);

myPromises
  .then((arrayOfValues) => {
    console.log(arrayOfValues);
  })
  .catch((rejectionReason) => {
    console.log(rejectionReason);
  });
```
Let’s break down what’s happening:

* We declare myPromises assigned to invoking `Promise.all()`.
* We invoke `Promise.all()` with an array of three promises— the returned values from functions.
* We invoke `.then()` with a success handler which will print the array of resolved values if each promise resolves successfully.
* We invoke `.catch()` with a failure handler which will print the first rejection message if any promise rejects.

 
  
  
  
  
  
  






