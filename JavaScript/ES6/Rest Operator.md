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
# DescriptionSection
A function's last parameter can be prefixed with `...` which will cause all remaining (user supplied) arguments to be placed within a "standard" javascript array. Only the last parameter can be a "rest parameter".
```
function myFun(a, b, ...manyMoreArgs) {
  console.log("a", a); 
  console.log("b", b);
  console.log("manyMoreArgs", manyMoreArgs); 
}

myFun("one", "two", "three", "four", "five", "six");

// Console Output:
// a, one
// b, two
// manyMoreArgs, [three, four, five, six]
```
### between rest parameters and the arguments objectSection
There are three main differences between rest parameters and the arguments object:

1. rest parameters are only the ones that haven't been given a separate name (i.e. formally defined in function expression), while the arguments object contains all arguments passed to the function;
2. the arguments object is not a real array, while rest parameters are Array instances, meaning methods like **sort, map, forEach or pop** can be applied on it directly;
3. the arguments object has additional functionality specific to itself (like the callee property).
