_from freeCodeCamp_
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

