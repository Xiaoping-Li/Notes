# Functions
Functions in JavaScript are declared using the `function` keyword. A function declaration creates a function that's a `Function 
object` having all the `properties, methods, and behaviors of Function objects`. By default, functions return the value `undefined`; to return any other value, the function must have a `return` statement that consists of the return keyword followed by the value to be returned (this can be a literal value, a variable, or even a call to a function).

## The Function Expression
A `function expression` is very similar to (and has almost the same syntax as) a `function statement`. The main difference between a _function expression_ and a _function statement_ is the **function name**, which can be omitted from a function expression to create an `anonymous function`. Function expressions are often used as _Immediately Invoked Function Expressions (IIFEs)_, which run as soon as they're defined.
* Unnamed Function Expression: The code below demonstrates an _unnamed_ function expression.
```
const square = function(x) {
  return x * x;
};
```
* Named Function Expression: The code below demonstrates a _named_ function expression.
```
const fib = function fibonacci(n){
    if (n > 2) {
        return fibonacci(n - 1) + fibonacci(n - 2);
    }
    else if (n < 1) {
        return 0;
    }
   
    return 1;
}
```

## Function Expression vs. Function Declaration
**Function Declaration**
```
function sayHi() {
  console.log('hello there!');
}
```

**Function Expression**
```
const sayHi = function(){
  console.log('hello there!');
}
```
Unlike `function declarations`, `function expression`s are not **hoisted** so they cannot be called before they are defined.

## Arrow Function
JavaScript also provides several ways to refactor _arrow function_ syntax. The most condensed form of the function is known as `concise body`. 
* Functions that take only a **single** parameter do not need that parameter to be enclosed in parentheses. However, if a function takes **zero or multiple** parameters, parentheses are `required`.
* A function body composed of a _single-line_ block does not need curly braces. Without the curly braces, whatever that line evaluates will be automatically _returned_. The contents of the block should immediately follow the arrow `=>` and the `return` keyword can be removed. This is referred to as _implicit return_.

# Recursion
This is an extremely important algorithmic concept that involves splitting a problem into two parts: a _base case_ and a _recursive case_. The problem is divided into smaller subproblems which are then solved recursively until such time as they are small enough and meet some base case; once the base case is met, the solutions for each subproblem are combined and their result is the answer to the entire problem. 


If the base case is not met, the function's recursive case calls the function again with modified values. The code must be structured in such a way that the base case is reachable after some number of iterations, meaning that each subsequent modified value should bring you closer and closer to the base case; otherwise, you'll be stuck in the dreaded infinite loop!


It's important to note that any task that can be accomplished recursively can also be performed iteratively (i.e., through a sequence of repeatable steps). Recursive solutions tend to be easier to read and understand than iterative ones, but there are often performance drawbacks associated with recursive solutions that you're going to want to evaluate on a case-by-case basis. Typically, we use recursion when each recursive call significantly reduces the size of the problem (e.g., if we can halve the dataset during each recursive call). Regardless of the advisability of recursively solving a problem, it's extremely important to practice and understand how to recursively solve problems.

