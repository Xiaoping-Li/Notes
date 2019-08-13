## Javascript Promises
One of the most commonly asked questions around Javascript is about Promises. Be prepared to write some code around promises in an interview. It’s also a good skill to have! You probably
want to review the following subjects:

### What is a promise?
A promise is an object which can be returned synchronously from an asynchronous function. It will be in one of 3 possible states:
* **Fulfilled**: onFulfilled() will be called (e.g., resolve() was called)
* **Rejected**: onRejected() will be called (e.g., reject() was called)
* **Pending**: not yet fulfilled or rejected

A promise is **settled** if it’s not pending (it has been resolved or rejected). Once settled, a promise can not be resettled. Calling `resolve()` or `reject()` again will have no effect. The immutability of a settled promise is an important feature.



### How do you write your own promise?
### How do you get the result of a promise (ex. from an API call)?
### How do you get the result from multiple promises in order (using Promise.all, etc.)?

