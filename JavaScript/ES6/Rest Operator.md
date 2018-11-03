In order to help us create more flexible functions, ES6 introduces the rest operator for function parameters. With the rest operator, you 
can create functions that take a variable number of arguments. These arguments are stored in an array that can be accessed later from 
inside the function.

The **rest parameter** syntax allows us to represent an indefinite number of arguments as an array.

The **rest operator** eliminates the need to check the args array and allows us to apply map(), filter() and reduce() on the parameters array.
```
function sum(...theArgs) {
  return theArgs.reduce((previous, current) => {
    return previous + current;
  });
}

console.log(sum(1, 2, 3));
// expected output: 6

console.log(sum(1, 2, 3, 4));
// expected output: 10
```
