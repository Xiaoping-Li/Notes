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
Javascript's ECMA6 came out with some cool new features; `...` is one of these new Javascript functionalities. It can be used in two different ways, as a `spread operator` OR as a `rest parameter`.
* `Rest parameter`: **collects** all _remaining_ elements into an _array_.
* `Spread operator`: allows _iterables_( arrays / objects / strings ) to be **expanded** into single arguments/elements.

* 1. **Rest parameter**
```
function add(x, y) {
  return x + y;
}

add(1, 2, 3, 4, 5) // returns 3
```
The above function call returns _3_, this is because in Javascript it is possible to call a function with any number of arguments. However, only the fist two arguments will be counted.

With `rest parameters` we can gather any number of arguments into an array and do what we want with them. So we can re-write the add function like this:
```
function add(...args) {
  let result = 0;

  for (let arg of args) result += arg;

  return result
}

add(1) // returns 1
add(1,2) // returns 3
add(1, 2, 3, 4, 5) // returns 15
```
**Note**: `Rest parameters` have to be at the **last argument**. This is because it collects all `remaining/ excess` arguments into an array. So having a function definition like this does not make sense and it errors out. :
```
function abc(a, ...b, c) {
  ...
  return;
}
```
We can separately define the _first arguments_, and the _rest of the arguments_ in the function call (no matter how many they are) will be collected into an array by the `rest parameter`.
```
function xyz(x, y, ...z) {
  console.log(x, ' ', y); // hey hello

  console.log(z); // ["wassup", "goodmorning", "hi", "howdy"]
  console.log(z[0]); // wassup
  console.log(z.length); // 4
}

xyz("hey", "hello", "wassup", "goodmorning", "hi", "howdy")
```
Since the `rest parameter` gives us an **array**, we can use array methods like `Array.find` e.t.c. Before `rest parameters` existed, to get all the arguments in a function we used `arguments` which is an _array-like object_.
```
function someFunction() {
  return arguments;
}

someFunction("joykare", 100, false);    // [Arguments] { '0': 'joykare', '1': 100, '2': false }
```
The downside of using the `arguments` keyword is that,
* It returns an _array-like_ object; this means you essentially cannot perform any `array-methods` like: `Array.filer`, `Array.map`.
* Another pitfall, is that we cannot use `arguments` in _arrow functions_. This is because _arrow-functions_ do not have their own `this`, and hence no `arguments` object either.

* 2. **Spread operator**
The `spread operator` allows us to **expand** elements. With `rest parameters` we were able to get a list of arguments into an array. `spread operators` however, let us **unpack** elements in an array to `single/individual` arguments.
  * 1. Adding array elements to an existing array
    ```
    const arr = ["Joy", "Wangari", "Warugu"];
    const newArr = ["joykare", ...arr];
    ```
    **Note**: Unlike `rest parameters` you can use the `spread operator` as the _first argument_. So if you wanted to add an element as the last element in your array you cna do this:
    ```
    const myNames = [...arr, "joykare"];
    ```  
  * 2. Copying arrays
    ```
    const arr = [1, 2, 3];
    const arr2 = [...arr];
    ```
  * 3. Pass elements of an array to a function as separate arguments
    ```
    function add(a, b, c) {
      return a + b + c ;
    }
    const args = [1, 2, 3];

    add(...args);
    ```
    **Note**: We have been using _arrays_ to demonstrate the `spread operator`, but any **iterable** also works. So, if we had a string `const str = 'joykare', [...str] translates to [ 'j', 'o', 'y', 'k', 'a', 'r', 'e' ]`.

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
