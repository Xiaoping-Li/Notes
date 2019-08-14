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


## Closures
Another topic commonly discussed in interviews, and is a bit more advanced, are closures. You will want to review:
http://javascriptissexy.com/understand-javascript-closures-with-ease/

Closures are used extensively in Node.js; they are workhorses in Node.js’ asynchronous, non-blocking architecture.

### What is a closure?
* **Closures** are inner functions inside of an outer function. They have their own local scope and has access to outer function's scope, parameters (but NOT arguments object), and they also have access to global variables. Closures is a neat way to deal with `scope` issues.
* A **closure** is an inner function that has access to the outer (enclosing) function's variables — _scope chain_. The `closure` has three _scope chains_: 
 * it has access to its own scope (variables defined between its curly brackets), 
 * it has access to the outer function's variables,
 * it has access to the global variables.
* The inner function has access not only to the outer function’s variables, but also to the outer function’s _parameters_. Note that the inner function **cannot** call the outer function’s arguments object, however, even though it can call the outer function’s parameters directly.
* You create a closure by adding a function inside another function. In JavaScript, closures are created every time a function is created, at function creation time.
* To use a closure, define a function inside another function and expose it. To expose a function, return it or pass it to another function.
* In JavaScript, closures are the primary mechanism used to enable _data privacy_. When you use closures for data privacy, the enclosed variables are only in scope within the containing (outer) function. You can’t get at the data from an outside scope except through the object’s privileged methods. 

### A common example question using a closure
```
// this inner function has access to the outer function's variables, including the parameter
function fullName (firstName, lastName) {
 const preIntro = "My name is: ";
 const combineIntro = () => preIntro + firstName + ' ' + lastName;
 return combineIntro();
}

fullName("leela", "Dee");
```

### Closures’ Rules and Side Effects
* Closures have access to the outer function’s variable even after the outer function returns:
 ```
 function scaleTenTwice(first) {
  const x = 10;
  
  // this inner function has access to the outer function's variables, including the parameter
  const secondScale = (second) => {
   return x * first * second;
  }
  return secondScale;
 }
 
 const nextScale = scaleTenTwice(2); // At this juncture, the scaleTenTwice outer function has returned.
 
 // The closure is called here after the outer function has returned above
 // Yet, the closure still has access to the outer function's variables and parameter
 nextScale(5);
 ```

* Closures store _references_ to the outer function’s variables. They do not store the actual value. Closures get more interesting when the value of the outer function’s variable changes before the closure is called. Such as this _private variables_ example:
 ```
 function fruitVending() {
  let fruit = "apple";
  
  return {
   getFruit: function() {
    return fruit;
   },
   
   setFruit: function(newType) {
    fruit = newType;
   }
  };
 }
 
 const vendingM = fruitVending();
 vendingM.getFruit(); // apple
 vendingM.setFruit("banana");
 vendingM.getFruit(); // banana
 ```
* Closures Gone Awry. Because closures have access to the updated values of the outer function’s variables, they can also lead to bugs when the outer function’s variable changes with a for loop.
```
function celebrityIDCreator (theCelebrities) {
    var i;
    var uniqueID = 100;
    for (i = 0; i < theCelebrities.length; i++) {
      theCelebrities[i]["id"] = function ()  {
        return uniqueID + i;
      }
    }
    
    return theCelebrities;
}

var actionCelebs = [{name:"Stallone", id:0}, {name:"Cruise", id:0}, {name:"Willis", id:0}];

var createIdForActionCelebs = celebrityIDCreator (actionCelebs);

var stalloneID = createIdForActionCelebs[0];
console.log(stalloneID.id()); // 103
```
In the preceding example, by the time the anonymous functions are called, the value of i is 3 (the length of the array and then it increments). The number 3 was added to the uniqueID to create 103 for ALL the celebritiesID. So every position in the returned array get id = 103, instead of the intended 100, 101, 102.

The reason this happened was because, as we have discussed in the previous example, the closure (the anonymous function in this example) has access to the outer function’s variables by reference, not by value. So just as the previous example showed that we can access the updated variable with the closure, this example similarly accessed the i variable when it was changed, since the outer function runs the entire for loop and returns the last value of i, which is 103.

**Note**: `let` can be used to avoid problems with closures. It binds fresh value rather than keeping an old reference as shown in examples below.
```
function celebrityIDCreator (theCelebrities) {
    var uniqueID = 100;
    for (let i = 0; i < theCelebrities.length; i++) {
      theCelebrities[i]["id"] = function ()  {
        return uniqueID + i;
      }
    }
    
    return theCelebrities;
}

var actionCelebs = [{name:"Stallone", id:0}, {name:"Cruise", id:0}, {name:"Willis", id:0}];

var createIdForActionCelebs = celebrityIDCreator (actionCelebs);

var stalloneID = createIdForActionCelebs[0];
console.log(stalloneID.id()); // 100
```

Or you can use an **Immediately Invoked Function Expression (IIFE)** to fix this side effect (bug) in closures, such as the following:
```
function celebrityIDCreator (theCelebrities) {
    var i;
    var uniqueID = 100;
    for (i = 0; i < theCelebrities.length; i++) {
        theCelebrities[i]["id"] = function (j)  { // the j parametric variable is the i passed in on invocation of this IIFE
            return function () {
                return uniqueID + j; // each iteration of the for loop passes the current value of i into this IIFE and it saves the correct value to the array
            } () // BY adding () at the end of this function, we are executing it immediately and returning just the value of uniqueID + j, instead of returning a function.
        } (i); // immediately invoke the function passing the i variable as a parameter
    }

    return theCelebrities;
}

var actionCelebs = [{name:"Stallone", id:0}, {name:"Cruise", id:0}, {name:"Willis", id:0}];

var createIdForActionCelebs = celebrityIDCreator (actionCelebs);

var stalloneID = createIdForActionCelebs [0];
console.log(stalloneID.id); // 100

var cruiseID = createIdForActionCelebs [1];
console.log(cruiseID.id); // 101
```






