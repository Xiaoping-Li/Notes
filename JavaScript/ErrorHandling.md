# Error Handling / Try, Catch, and Finally

## Error
There are three types of errors in programming:

### 1. Syntax Error (Parsing Error)
In a traditional programming language, this type of error occurs at _compile time_; because JavaScript is an _interpreted language_, this type of error arises when the code is interpreted. When a syntax error occurs in JavaScript, only the code contained within the same _thread_ as the syntax error is affected; independent code running in other threads will still be executed, as nothing in them depends on the code containing the error. For example, consider the following code containing a syntax error:
```
console.log("Hello" 
```
This produces the following error: `SyntaxError: missing ) after argument list`. This is because we failed to add a closing parenthesis to our call to _console.log_.

### 2. Runtime Error (Exception)
Commonly referred to as _exceptions_, this type of error occurs during execution (i.e., after compilation or interpretation). Once a runtime error is encountered, an exception is _thrown_ in the hope that it will be _caught_ by a subsequent section of code containing instructions on how to recover from the error. Much like syntax errors, these affect the thread where they occured but allow other, independent threads to continue normal execution. For example, consider the following code containing a runtime error:
```
function sum(a, b) {}
add(2, 3) 
```
This produces the following error: `ReferenceError: add is not defined`. This is because we attempted to call the _add_ function without ever declaring and defining it.

### 3. Logical Error
These are some of the most difficult errors to isolate because they cause the program to operate without terminating or crashing, but the operations the code performs are not correct. Unlike syntax and runtime errors which arise due to some violation of the rules of the language, these errors occur when there is a mistake in your the code's logic.

**Tip**: When trying to isolate logical errors in code, it's often helpful to print the contents of your variables to _stderr (standard error)_ at various stages in the logic using `console.warn()` or `console.error()`. For example, if we used this version of the sum function instead:
```
function sum(a, b) {
    var result = a - b;
    console.error("The sum of " + a + " and " + b + " is " + result);
    return result;
}
```
The following line would be printed to our error console during execution: `The sum of 2 and 3 is -1.` This makes it obvious during debugging that there is a logical issue with how our function calculates the sum of a and b.

## Try, Catch, and Finally








