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
The _try_ statement has three forms:

* _try-catch_
* _try-finally_
* _try-catch-finally_

### _try_ block
The _try_ block is the first step in error handling and is used for any block of code that is likely to raise an exception. It should contain one or more statements to be executed and is typically followed by at least one _catch clause_ and/or the optional _finally clause_. 

### _catch_ block
The _catch_ block immediately follows the _try_ block and is executed only if an exception is thrown when executing the code within the _try_ block. It contains statements specifying how to proceed and recover from the thrown exception; if no exception is thrown when executing the _try_ block, the _catch_ block is skipped. If any statement within the _try_ block (including a function call to code outside of the block) throws an exception, control immediately shifts to the catch clause.

It's important to note that we always want to avoid throwing an exception. It's best if the contents of the _try_ block execute without issue but, if an exception is unavoidable, control passes to the _catch_ block which should contain instructions that report and/or recover from the exception.

### _finally_ block
The _finally_ block is optional. It executes after the _try_ and _catch_ blocks, but before any subsequent statements following these blocks. The _finally_ block always executes, regardless of whether or not an exception was thrown or caught.

## Throw
We use the _throw_ statement, denoted by the `throw` keyword, to throw an exception. There are two ways to do this, shown below.

### 1. `throw value`
We can throw an exception by following the keyword `throw` with some `value` that we wish to use for the exception being thrown. Click Run below to see this in code.

### 2. `throw new Error(customError)`
We can throw an exception by following the keyword `throw` with `new Error(customError)`, where _customError_ is the value we want for the _message_ property of the exception being thrown. 

```
function isPositive(a) {
    if (a > 0) {
        return 'YES';
    } else if (a === 0) {
        throw new Error('Zero Error');
    } else {
        throw new Error('Negative Error');
    }    
}

try {
    isPositive(0); 
}
catch(e) {
    console.log(e.message);
}
```
 

## Example
https://www.hackerrank.com/challenges/js10-try-catch-and-finally/topics/javascript-strings

**Task**

Complete the reverseString function; it has one parameter, . You must perform the following actions:

1. Try to reverse string _s_ using the split, reverse, and join methods.
1. If an exception is thrown, catch it and print the contents of the exception's _message_ on a new line.
1. Print _s_ on a new line. If no exception was thrown, then this should be the reversed string; if an exception was thrown, this should be the original string.

```
function reverseString(s) {
    let rtn = s;
    try {
        rtn = s.split('').reverse().join('');
    }
    catch (e) {
        console.log(e.message);
    }
    finally {
        console.log(rtn);
    }   
}
```


