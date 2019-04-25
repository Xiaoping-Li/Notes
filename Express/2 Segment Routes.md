# Routers
The Expressions/Animals routes are all working well, and our machine is fully functional! Our **app.js** file, however, is getting quite long and hard to read. It’s easy to imagine that as we add functionality to an application, this file would get long and cumbersome.

Luckily, Express provides functionality to alleviate this problem: **Routers**. **Routers** are mini versions of Express applications — they provide functionality for handling route matching, requests, and sending responses, but they _do not_ start a separate server or listen on their own ports. Routers use all the `.get()`, `.put()`, `.post()`, and `.delete()` routes that you know and love.

In this lesson, we will use **Routers** to clean up our code and separate our application into a file to handle all `/expressions` routes, and another to handle all `/animals` routes.

## Express.Router
An Express router provides a subset of Express methods. To create an instance of one, we invoke the `.Router()` method on the top-level Express import.

To use a router, we mount it at a certain path using `app.use()` and pass in the router as the second argument. This router will now be used for all paths that begin with that path segment. To create a router to handle all requests beginning with `/monsters`, the code would look like this:
```
const express = require('express');
const app = express();

const monsters = {
  '1': {
    name: 'godzilla',
    age: 250000000
  },
  '2': {
    Name: 'manticore',
    age: 21
  }
}

const monstersRouter = express.Router();

app.use('/monsters', monstersRouter);

monstersRouter.get('/:id', (req, res, next) => {
  const monster = monsters[req.params.id];
  If (monster) {
    res.send(monster);
  } else {
    res.status(404).send();
  }
});
```
Inside the _monstersRouter_, all matching routes are assumed to have `/monsters` prepended, as it is _mounted_ at that path. `monstersRouter.get('/:id')` matches the full path `/monsters/:id`.

## Using Multiple Router Files
Generally, we will keep each router in its own file, and require them in the main application. This allows us to keep our code clean and our files short.

To do this with `monstersRouter`, we would create a new file **monsters.js** and move all code related to /monsters requests into it.
```
// monsters.js
const express = require('express');
const monstersRouter = express.Router();

const monsters = {
  '1': {
    name: 'godzilla',
    age: 250000000
  },
  '2': {
    Name: 'manticore',
    age: 21
  }
}

monstersRouter.get('/:id', (req, res, next) => {
  const monster = monsters[req.params.id];
  if (monster) {
    res.send(monster);
  } else {
    res.status(404).send();
  }
});

module.exports = monstersRouter;
```
This code contains all the monsters specific code. In a more full-fledged API, this file would contain multiple routes. To use this router in another file, we use `module.exports` so that other files can access `monstersRouter`. The only other new line of code required is that Express must be `required` in each file, since we’ll need to create a router with `express.Router()`.

Our **main.js** file could then be refactored to import the `monstersRouter`:
```
const express = require('express');
const app = express();
const monstersRouter = require('./monsters.js');

app.use('/monsters', monstersRouter);
```
