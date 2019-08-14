## JavaScript Hoisting
(https://wsvincent.com/javascript-hoisting/)

`Hoisting` is a behavior in JavaScript where variable and function _declarations_ are moved to the top of their scope before code execution. 
* JavaScript `Declarations` by `var` are _Hoisted_.
* JavaScript `Initializations` are Not _Hoisted_.
* Variables and constants declared with `let` or `const` are not hoisted.


## ES6
Some companies want to test your knowledge specifically about modern Javascript. Some example questions are:
### What is your favourite feature of ES6?
#### `let` and `const`
(https://codeutopia.net/blog/2015/01/06/es6-what-are-the-benefits-of-the-new-features-in-practice/)

* The `let` keyword defines a _block-scoped_ variable. Block-scoped means the declaration is only available within a so-called “block”.
* `const` declares a _block-scoped_ constant. A constant is like a variable, except you can’t change its value.
*  When assigning an object to a `const`, you will still be able to modify its properties!
* Variables and constants declared with `let` or `const` are not hoisted!

```
function foo() {
  //whenever we have curly braces in code, it defines a "block"
  {
    console.log(hi); //error, the variable is not defined
 
    //this is only available within this block
    let hi = 1;
  }
  console.log(hi); //output: Error, hi is not defined
 
  for(let i = 0; i < 10; i++) {
    //the variable `i` is only available within the for block
  }
 
  console.log(i); //output: Error, i is not defined
}
```
Swap in some `var`s instead of `let`s…
```
function foo() {
 
  {
    //with var, the variable declaration gets hoisted so we will not get an error
    //when attempting to use it before its declaration appears in code
    console.log(hi); //output: undefined
 
    var hi = 1;
  }
  console.log(hi); //output: 1
 
  for(var i = 0; i < 10; i++) {
    //the variable `i` is only available within the for block
  }
 
  console.log(i); //output: 10
}
```

#### Benefits of `let`
A major benefit of `let` is it works nicely within for-loops. One of the most common stumbling blocks for JS-beginners is the closure-within-for problem.

#### Benefits of `const`
* The person reading the code immediately sees the variable should not be changed
* Changing the value will result in an error

### Default parameters



### What are the benefits of an arrow function?
### Async and Await keywords
### Javascript classes
### Here are a couple over common ES6 questions
