_from freeCodeCamp & HackerRank_
# Variable Declaration Keywords
## var
We use the _var_ keyword to declare variables. The **scope** of a variable declared using this keyword is `within the context wherever it was declared`. For variables declared outside any function, this means they are globally available throughout the program. For variables declared within a function, this means they are only available within the function itself.

## let
We use the _let_ keyword to declare variables that are `limited in scope to the block, statement, or expression in which they are used`. This is unlike the _var_ keyword, which defines a variable globally or locally to an entire function regardless of block scope.


It's important to note that you cannot redeclare a variable declared using the let keyword within the same scope as the original variable. An attempt to do this raises an Error, as demonstrated by the code below.

## const
We use the _const_ keyword to create a _read-only_ reference to a value, meaning the value referenced by this variable cannot be reassigned. Because the value referenced by a constant variable cannot be reassigned, JavaScript **requires** that constant variables always be initialized.

# Declaration
One of the biggest problems with declaring variables with the **var** keyword is that you can overwrite variable declarations without an error.
```
var camper = 'James';
var camper = 'David';
console.log(camper);
// logs 'David'
```
When your code becomes larger, you might accidentally overwrite a variable that you did not intend to overwrite.Because this behavior does 
not throw an error, searching and fixing bugs becomes more difficult.

A new keyword called **let** was introduced in _ES6_ to solve this potential issue with the **var** keyword.

If you were to replace **var** with **let** in the variable declarations of the code above, the result would be an error.
```
let camper = 'James';
let camper = 'David'; // throws an error
This error can be seen in the console of your browser.
```
So unlike var, `when using let, a variable with the same name can only be declared once`.

# Scope
When you declare a variable with the **var** keyword, it is declared globally, or locally if declared inside a function.

The **let** keyword behaves similarly, but with some extra features. `When you declare a variable with the let keyword inside a block, statement, or expression, its scope is limited to that block, statement, or expression.`
For example:
```
var numArray = [];
for (var i = 0; i < 3; i++) {
  numArray.push(i);
}
console.log(numArray);
// returns [0, 1, 2]
console.log(i);
// returns 3
```
With the var keyword, **i** is declared globally. So when i++ is executed, it updates the global variable. This behavior will cause problems if you were to create a function and store it for later use inside a for loop that uses the i variable. This is because the stored function will always refer to the value of the updated global i variable.
```
var printNumTwo;
for (var i = 0; i < 3; i++) {
  if(i === 2){
    printNumTwo = function() {
      return i;
    };
  }
}
console.log(printNumTwo());
// returns 3
```
As you can see, **printNumTwo()** prints 3 and not 2. This is because the value assigned to i was updated and the printNumTwo() returns the **global i** and not the value i had when the function was created in the for loop. The let keyword does not follow this behavior:
```
'use strict';
let printNumTwo;
for (let i = 0; i < 3; i++) {
  if (i === 2) {
    printNumTwo = function() {
      return i;
    };
  }
}
console.log(printNumTwo());
// returns 2
console.log(i);
// returns "i is not defined"
```
**i** is not defined because it was not declared in the global scope. It is only declared within the for loop statement. printNumTwo() returned the correct value because three different i variables with unique values (0, 1, and 2) were created by the let keyword within the loop statement.
# Const
**const** has all the awesome features that **let** has, with the added bonus that variables declared using **const** are **read-only**. They are a constant value, which means that once a variable is assigned with const, it cannot be reassigned.
```
"use strict"
const FAV_PET = "Cats";
FAV_PET = "Dogs"; // returns error
```
As you can see, trying to reassign a variable declared with `const` will throw an error. You should always name variables you don't want to reassign using the `const` keyword. This helps when you accidentally attempt to reassign a variable that is meant to stay constant. `A common practice when naming constants is to use all uppercase letters, with words separated by an underscore.`
## Some developers prefer to assign all their variables using const by default, unless they know they will need to reassign the value. Only in that case, they use let.

However, it is important to understand that objects (including arrays and functions) assigned to a variable using **const** are still mutable. `Using the const declaration only prevents reassignment of the variable identifier.`
```
"use strict";
const s = [5, 6, 7];
s = [1, 2, 3]; // throws error, trying to assign a const
s[2] = 45; // works just as it would with an array declared with var or let
console.log(s); // returns [5, 6, 45]
```
As you can see, you can mutate the object [5, 6, 7] itself and the variable s will still point to the altered array [5, 6, 45]. Like all arrays, the array elements in s are mutable, `but because const was used, you cannot use the variable identifier s to point to a different array using the assignment operator.`
## const declaration alone doesn't really protect your data from mutation. To ensure your data doesn't change, JavaScript provides a function Object.freeze to prevent data mutation.

`Once the object is frozen, you can no longer add, update, or delete properties from it. Any attempt at changing the object will be rejected without an error.`
```
let obj = {
  name:"FreeCodeCamp",
  review:"Awesome"
};
Object.freeze(obj);
obj.review = "bad"; //will be ignored. Mutation not allowed
obj.newProp = "Test"; // will be ignored. Mutation not allowed
console.log(obj); 
// { name: "FreeCodeCamp", review:"Awesome"}
```

