# Javascript Specifics
Javascript is a funny language with many weird parts about it. Sometimes companies want to test your knowledge of specifics around the language:
## Here are some example questions 
(https://github.com/h5bp/Front-end-Developer-Interview-Questions/blob/master/src/questions/javascript-questions.md)

Some confusing concepts are the `this` keyword, `event delegation`, `hoisting`, `undefined vs. null` etc.

## Here are more examples 
(https://www.toptal.com/javascript/interview-questions)

## Callbacks
In JavaScript, _functions_ are objects. Because of this, functions can take functions as _arguments_, and can be returned by other functions. Functions that do this are called **higher-order functions**. Any function that is passed as an argument is called a **callback function**.

Callbacks are a way to make sure certain code doesn’t execute until other code has already finished execution. When you make requests to an API, you have to wait for the response before you can act on that response. This is a wonderful example of a real-world callback.

A callback is important here because we need to wait for a response from the server before we can move forward in our code. We don’t know if our API request is going to be successful or not so after sending our parameters to server via a get request, we wait. Once server responds, our _callback_ function is invoked. Server will either send an `err (error)` object or a response object back to us. In our callback function we can use an `if()` statement to determine if our request was successful or not, and then act upon the new data accordingly.

## Functional programming 

(https://medium.com/javascript-scene/master-the-javascript-interview-what-is-functional-programming-7f218c68b3a0)
