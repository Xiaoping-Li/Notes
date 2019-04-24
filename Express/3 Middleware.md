# Middleware 
1. [next()](#next)
2. [Request And Response Parameters](#Request)
3. [Route-Level app.use() - Single Path](#Single)
4. [Control Flow With next()](#Control)
5. [Route-Level app.use() - Multiple Paths](#Multiple)
6. [Middleware Stacks](#Middleware)
7. [Open-Source Middleware](#Open-Source)

So how do we get code to run every time one of our Express routes is called without repeating ourselves? We write something called _middleware_. **Middleware** is code that executes _between_ a server `receiving a request and sending a response`. It operates on the boundary, so to speak, between those two HTTP actions.

In Express, middleware is a function. **Middleware** can perform logic on the request and response objects, _such as_: inspecting a request, performing some logic based on the request, attaching information to the response, attaching a status to the response, sending the response back to the user, or simply passing the request and response to another middleware. Middleware can do any combination of those things or anything else a Javascript function can do.
```
app.use((req, res, next) => {
  console.log(`${req.method} Request Received`);
});
```
`app.use()` takes a callback function that it will call for `every received request`. In this example, every time the server receives a request, it will find the first registered middleware function and call it. In this case, the server will find the callback function specified above, call it, and print out 'Request received'.

You might be wondering what else our application is responsible for that isn’t related to middleware. The answer is not much. To quote the Express documentation:

_An Express application is essentially a series of middleware function calls._

It is precisely this service that we leverage Express for. In addition to performing the routing that allows us to communicate appropriate data for each separate endpoint, we can perform application logic we need by implementing the necessary middleware.

## next() <a name="next"></a>
The middleware stack is processed `in the order they appear` in the application file, such that _middleware defined later happens after middleware defined before_. It’s **important** to note that this is regardless of method — an `app.use()` that occurs after an `app.get()` will get called after the `app.get()`. Observe the following code:
```
app.use((req, res, next) => {
  console.log("A sorcerer approaches!");
  next();
});

app.get('/magic/:spellname', (req, res, next) => {
  console.log("The sorcerer is casting a spell!");
  next();
});

app.get('/magic/:spellname', (req, res, next) => {
  console.log(`The sorcerer has cast ${req.params.spellname}`);
  res.status(200).send();
});

app.get('/magic/:spellname', (req, res, next) => {
  console.log("The sorcerer is leaving!");
});

// Accessing http://localhost:4001/magic/fireball 
// Console Output:
// "A sorcerer approaches!"
// "The sorcerer is casting a spell!"
// "The sorcerer has cast fireball"
```
In the above code, the routes are called in the order that they appear in the file, provided the previous route called `next()` and thus passed control to the next middleware. We can see that the final matching call was not printed. This is because the previous middleware did not invoke the `next()` function to run the following middleware.

An **Express middleware** is a function with three parameters: `(req, res, next)`. The sequence is expressed by a set of callback functions invoked _progressively_ after each middleware performs its purpose. The third argument to a middleware function, `next`, should get _explicitly_ called as the last part of the middleware’s body. This will hand off the processing of the request and the construction of the response to the next middleware in the stack.

## Request And Response Parameters <a name="Request"></a>
Recall the function signature of an Express middleware, i.e., `(req, res, next)`. You might recognize this signature as being the very same that we’ve used for Express routes in the past. Well there’s a perfectly good reason for that: _Express routes are middleware_. Every route created in Express is also a middleware function handling the request and response objects at that part of the stack. Express routes also have the option of sending a response body and status code and closing the connection. These two features are a byproduct of Express routes being middleware, because all Express middleware functions have access to the request, the response, and the next middleware in the stack.

## Route-Level app.use() - Single Path <a name="Single"></a>
Let’s see what the Express documentation for `app.use()` function signature: `app.use([path,] callback [, callback...])`.
 
In documentation for many programming languages, optional arguments for functions are placed in square brackets (`[]`). This means that `app.use()` takes an optional path parameter as its first argument. We can now write middleware that will run for every request at a specific path.
```
app.use('/sorcerer', (req, res, next) => {
  console.log('User has hit endpoint /sorcerer');
  next();
});
```
In the example above the _console_ will print `'User has hit endpoint /sorcerer'`, if someone visits our web page’s `‘/sorcerer’` endpoint. Since the method `app.use()` was used, it won’t matter if the user is performing a `GET`,a `POST`, or any other kind of _HTTP request_. Since the path was given as an argument to `app.use()`, this middleware function will not execute if the user hits a different path (for instance: `'/spells'` or `'/sorcerer/:sorcerer_id'`).
```
app.use('/beans/:beanName', (req, res, next) => {
  const beanName = req.params.beanName;
  if (!jellybeanBag[beanName]) {
    console.log('Response Sent');
    return res.status(404).send('Bean with that name does not exist');
  }
  
  /*
  After the checking logic, we’re going to attach the correct bean object to the request by setting a bean property on the request (`req.bean`). Set it equal to the correct bean from the bean object. For good measure, also attach the bean name to the request as req.beanName.
  */
  req.bean = jellybeanBag[beanName];
  req.beanName = beanName;
  next();
});
```

## Control Flow With next() <a name="Control"></a>
We’ve experienced writing middleware that performs its function and hands off the request and response objects to the next function in the stack, but why exactly do we have to write `next()` at the end of every middleware? If it always needs to be at the end of every function we write, it seems like an unnecessary piece of boilerplate. You might be surprised to learn that we aren’t going to introduce a way to automatically hand off the request and response objects without having to repeatedly write `next()`. Rather, we’re going to explore why it is useful to have `next()` as a separate function call. _The biggest reason being we don’t always want to pass control to the next middleware in the stack_.

For example, when designing a system with confidential information, we want to be able to selectively show that information to authorized users. In order to do that, we would create middleware that tests a user’s permissions. If the user has the permission necessary, we would continue through the middleware stack by calling `next()`. If it fails, we would want to let the user know that they’re not allowed to see the information they’re trying to access.

## Route-Level app.use() - Multiple Paths <a name="Multiple"></a>
We learned that `app.use()` takes a **path** parameter, but we never fully investigated what that path parameter could be. Let’s take another look at the Express documentation for `app.use()`:
```
“argument: path

description: The path for which the middleware function is invoked; can be any of:

A string representing a path.
A path pattern.
A regular expression pattern to match paths.
An array of combinations of any of the above. “
```
So `app.use()` can take an array of paths! That seems like a handy way to rewrite the code from our last exercise so that we don’t have to put the same code in two different routes with different paths.

## Middleware Stacks <a name="Middleware"></a>
Recall that middleware is just a function with a specific signature, namely `(req, res, next)`. We have, for the most part, been using anonymous function definitions for this because our middleware has only been relevant to the route invoking it. There is nothing stopping us from defining functions and using them as middleware though. It is also modifiable so that you can remove the `app.use()` line and replace it with a specific route method, or sprinkle it throughout the application without it being universal.

Up until this point we’ve only been giving each middleware-accepting method a single callback. With modular pieces like this, it is useful to know that methods such as `app.use()`, `app.get()`, `app.post()`, and so on all can take multiple callbacks as additional parameters. This results in code that looks like the following:
```
const authenticate = (req, res, next) => {
  ...
};

const validateData = (req, res, next) => {
  ...
};

const getSpell = (req, res, next) => {
  res.status(200).send(getSpellById(req.params.id));
};

const createSpell = (req, res, next) => {
  createSpellFromRequest(req);
  res.status(201).send();
};

const updateSpell = (req, res, next) => {
  updateSpellFromRequest(req);
  res.status(204).send();
}

app.get('/spells/:id', authenticate, getSpell);

app.post('/spells', authenticate, validateData, createSpell);

app.put('/spells/:id', authenticate, validateData, updateSpell);
```
In the above code sample, we created reusable middleware for authentication and data validation. We use the `authenticate()` middleware to verify a user is logged in before proceeding with the request and we use the `validateData()` middleware before performing the appropriate _create_ or _update_ function. Additional middleware can be placed at any point in this chain.

## Open-Source Middleware <a name="Open-Source"></a>
### Logging
We will replace the logging code in the workspace with **morgan**, an open-source library for _logging information about the HTTP request-response cycle in a server application_. `morgan()` is a function that will return a middleware function, to reiterate: the return value of `morgan()` will be a function, that function will have the function signature `(req, res, next)` that can be inserted into an `app.use()`, and that function will be called before all following middleware functions. **Morgan** takes an argument to describe the formatting of the logging output. For example, `morgan('tiny')` will return a middleware function that does a “tiny” amount of logging. With morgan in place, we’ll be able to remove the existing logging code. Once we see how fast it is to add logging with morgan, we won’t have to spend time in the future trying to figure out how to replicate that functionality.
```
const morgan = require('morgan');
app.use(morgan('tiny'));
```

### Body Parsing
When we implement middleware, we take in the `req` object, so that we can see information about the request. This object includes a good deal of important information about the request that we can use to inform our response, however for some requests it misses a fundamental piece. An HTTP request can include a _body_, a set of information to be transmitted to the server for processing. This is useful when the end user needs to send information to the server. If you’ve ever uploaded a post onto a social media website or filled out a registration form chances are you’ve sent an HTTP request with a body. The lucky thing about using open-source middleware is that even though parsing the body of an HTTP request is a tricky operation requiring knowledge about network data transfer concepts, we easily manage it by importing a library to do it for us.
```
const bodyParser = require('body-parser');
app.use(bodyParser.json());
```

### Error-Handling Middleware
When an error is thrown somewhere in our code, we want to be able to communicate that there was a problem to the user. **Error handling middleware** needs to be the last `app.use()` in your file. If an error happens in any of our routes, we want to make sure it gets passed to our error handler. The middleware stack progresses through routes as they are presented in a file, _therefore the error handler should sit at the bottom of the file_. 
```
app.use((err, req, res, next) => {
  console.error(err.stack);
  res.status(500).send('Something broke!');
});
```
Based on the code above, we can see that error-handling middleware is written much like other kinds of middleware. The biggest difference is that there is an additional parameter in our callback function, `err`. This represents the error object, and we can use it to investigate the error and perform different tasks depending on what kind of error was thrown. For now, we only want to send an HTTP 500 status response to the user.

Express has its own error-handler, which catches errors that we haven’t handled. But if we anticipate an operation might fail, we can invoke our error-handling middleware. We do this by passing an `error` object as an argument to `next()`. Usually, `next()` is called without arguments and will proceed through the middleware stack as expected. When called with an error as the first argument, however, it will call any applicable error-handling middleware.
```
app.use((req, res, next) => {
  const newValue = possiblyProblematicOperation();
  if (newValue === undefined) {
    let undefinedError = new Error('newValue was not defined!');
    undefinedError.status = 404; // Corresponding status here to pass down
    return next(undefinedError);
  }
  next();
});

app.use((err, req, res, next) => {
  const status = err.status || 500;
  res.status(status).send(err.message);
});
```
In this segment we assign the return value of the function `possiblyProblematicOperation()` to `newValue`. Then we check to see if this function returned anything at all. If it didn’t, we create a `new Error` and pass it to `next()`. This prompts the error-handling middleware to send a response back to the user, but many other error-handling techniques could be employed (like logging, re-attempting the failed operation, and/or emailing the developer).

###Discovering Open-Source Middleware
list of Express middleware (https://expressjs.com/en/resources/middleware.html)
