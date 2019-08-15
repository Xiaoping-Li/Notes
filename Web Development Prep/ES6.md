## JavaScript Hoisting
(https://wsvincent.com/javascript-hoisting/)

`Hoisting` is a behavior in JavaScript where variable and function _declarations_ are moved to the top of their scope before code execution. 
* JavaScript `Declarations` by `var` are _Hoisted_.
* JavaScript `Initializations` are Not _Hoisted_.
* Variables and constants declared with `let` or `const` are not hoisted.


## ES6
Some companies want to test your knowledge specifically about modern Javascript. Some example questions are:
### What is your favourite feature of ES6?

#### 1. `let` and `const`
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

**Benefits of `let`**
A major benefit of `let` is it works nicely within for-loops. One of the most common stumbling blocks for JS-beginners is the closure-within-for problem.

**Benefits of `const`**
* The person reading the code immediately sees the variable should not be changed
* Changing the value will result in an error

#### 2. Arrow Function
* Arrow syntax automatically binds `this` to the surrounding code’s context
* The syntax allows an implicit return when there is no body block, resulting in shorter and simpler code in some cases
* `=>` is shorter and simpler than `function`

#### 3. Promise (See Promises.md)
#### 4. Template literals
(https://codeburst.io/javascript-what-are-template-literals-5d08a50ef2e3)

`Template literals` are quite simply the easiest way to improve your JavaScript code **readability** when working with _Strings_.
* A `template` is a _preset_ format.
* A `literal` is a value written exactly as it’s meant to be interpreted.

**Benefits**:
* When you want to use variables within strings. `${}`
* `Line breaks` are another area where template literals can truly shine. With template literals, all `new line characters, tabs, spaces`, etc. inserted in the source become a part of the string.

#### 5. Destructuring assignment
`Destructuring assignment` allows you to assign the properties of an array or object to variables using syntax that looks similar to array or object literals.

```
const [first, second, third] = someArray;
const {name, email, phone} = user;
```
* 1. Destructuring arrays and iterables
  * 1. You can nest patterns as deep as you would like:
    ```
    const [foo, [[bar], baz]] = [1, [[2], 3]];
    console.log(foo);   // 1
    console.log(bar);   // 2
    console.log(baz);   // 3
    ```
  * 2. You can skip over items in the array being destructured:
    ```
    const [,,third] = ["foo", "bar", "baz"];
    console.log(third);   // "baz"
    ```
  * 3. And you can capture all trailing items in an array with a “rest” pattern:
    ```
    const [head, ...tail] = [1, 2, 3, 4];
    console.log(tail);   // [2, 3, 4]
    ```
  * 4. When you access items in the array that are out of bounds or don’t exist, you get the same result you would by indexing: `undefined`.
    ```
    console.log([][0]);   // undefined
    
    var [missing] = [];
    console.log(missing);   // undefined
    ```
* 2. Destructuring objects
Destructuring on objects lets you bind variables to different properties of an object. You specify the property being bound, followed by the variable you are binding its value to.
```
var robotA = { name: "Bender" };
var robotB = { name: "Flexo" };

var { name: nameA } = robotA;
var { name: nameB } = robotB;

console.log(nameA);   // "Bender"
console.log(nameB);   // "Flexo"
```
  * 1. There is a helpful syntactical shortcut for when the property and variable names are the same:
    ```
    var { foo, bar } = { foo: "lorem", bar: "ipsum" };
    ```
  * 2. And just like destructuring on arrays, you can nest and combine further destructuring:
    ```
    var complicatedObj = {
      arrayProp: [
        "Zapp",
        { second: "Brannigan" }
      ]
    };

    var { arrayProp: [first, { second }] } = complicatedObj;

    console.log(first);   // "Zapp"
    console.log(second);   // "Brannigan"
    ```
  * 3. When you destructure on properties that are not defined, you get undefined:
    ```
    var { missing } = {};
    console.log(missing);   // undefined
    ```
    
#### 6. Three dots (...): Rest parameter Or Spread operators
Javascript's ECMA6 came out with some cool new features; `...` one of these new Javascript functionalities. It can be used in two different ways; as a spread operator OR as a rest parameter.




#### 7. Default parameters
ES6 allows us to define _default values_ for function parameters! One potential gotcha of this syntax is that variables without default parameters still receive `undefined` as their default, rather than throwing an error if not called with enough parameters. 
```
function hello(name = 'Anonymous') {
  console.log('Hi ' + name);
}
```
**Benefits**:
* Less boilerplate code to handle parameters
* Anyone reading your code immediately sees which parameters are optional, without having reading the function body (where they might or might not be on top of the function).
* This can be useful when refactoring, as you can change a function to have default parameters instead of removing a parameter altogether to keep better backwards-compatibility

#### 8. Iterators and Generators


### What are the benefits of an arrow function?
### Async and Await keywords
### Javascript classes
### Here are a couple over common ES6 questions
