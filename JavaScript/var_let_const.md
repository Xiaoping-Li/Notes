_from freeCodeCamp_
# Declaration
One of the biggest problems with declaring variables with the var keyword is that you can overwrite variable declarations without an error.
```
var camper = 'James';
var camper = 'David';
console.log(camper);
// logs 'David'
```
When your code becomes larger, you might accidentally overwrite a variable that you did not intend to overwrite.Because this behavior does 
not throw an error, searching and fixing bugs becomes more difficult.
