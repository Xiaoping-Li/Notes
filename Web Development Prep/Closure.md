# Closures
Another topic commonly discussed in interviews, and is a bit more advanced, are closures. You will want to review:
http://javascriptissexy.com/understand-javascript-closures-with-ease/

Closures are used extensively in Node.js; they are workhorses in Node.js’ asynchronous, non-blocking architecture.

## What is a closure?
* **Closures** are inner functions inside of an outer function. They have their own local scope and has access to outer function's scope, parameters (but NOT arguments object), and they also have access to global variables. Closures is a neat way to deal with `scope` issues.
* A **closure** is an inner function that has access to the outer (enclosing) function's variables — _scope chain_. The `closure` has three _scope chains_: 
 * it has access to its own scope (variables defined between its curly brackets), 
 * it has access to the outer function's variables,
 * it has access to the global variables.
* The inner function has access not only to the outer function’s variables, but also to the outer function’s _parameters_. Note that the inner function **cannot** call the outer function’s arguments object, however, even though it can call the outer function’s parameters directly.
* You create a closure by adding a function inside another function. In JavaScript, closures are created every time a function is created, at function creation time.
* To use a closure, define a function inside another function and expose it. To expose a function, return it or pass it to another function.
* In JavaScript, closures are the primary mechanism used to enable _data privacy_. When you use closures for data privacy, the enclosed variables are only in scope within the containing (outer) function. You can’t get at the data from an outside scope except through the object’s privileged methods. 
```
// this inner function has access to the outer function's variables, including the parameter
function fullName (firstName, lastName) {
 const preIntro = "My name is: ";
 const combineIntro = () => preIntro + firstName + ' ' + lastName;
 return combineIntro();
}

fullName("leela", "Dee");
```

## A common example question using a closure
JavaScript Closures: setTimeout Inside a For Loop (https://wsvincent.com/javascript-closure-settimeout-for-loop/)

It’s a common question asked in interviews since the answer touches upon several core JavaScript concepts: `closures`, `hoisting`, and the `event loop`.

```
// var defined a function scope variable here
for (var i = 1; i < 5; i++) {
  console.log(i);  // 1 2 3 4
}

// for loop will be executed first, closure functions will be waiting in the callback queue, and will be invoked after i incremented to 5
for (var i = 1; i < 5; i++) {
    setTimeout(() => console.log(i), 1000)  // 5 5 5 5
}

//Solution 1: let defines a enclosing block scope variable, which binds with fresh value
for (let i = 1; i < 5; i++) {
    setTimeout(() => console.log(i), 1000)  // 1 2 3 4
}

// Solution 2: Immediately Invoked Function Expression (IIFE)
for (var i = 0; i < 5; i++) {
  (function (idx) {
    setTimeout(
    () => console.log(idx), 
    1000
  );
  })(i); 
}
```

## Closures’ Rules and Side Effects
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
