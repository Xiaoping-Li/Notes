# Express

1. [Starting A Server](#Starting)
2. [Writing Routes](#Writing)
3. [Sending A Response](#Sending)
4. [Matching Route Paths](#Matching)
5. [Route parameters](#Route)
6. [Setting Status Codes](#Setting)
7. [Matching Longer Paths](#MatchingLonger)
8. [Other HTTP Methods](#OtherMethods)
    1. [Using Queries](#UsingQueries)
    2. [Creating An Expression](#CreatingExpression)
    3. [Deleting Old Expressions](#Deleting)

A huge portion of the Internet’s data travels over _HTTP/HTTPS_ through `request-response` cycles between _clients and servers_. Every time that you use a website, your browser sends requests to one or many servers requesting resources.

**Express** is a powerful but flexible Javascript _framework_ for creating `web servers and APIs`. It can be used for everything from simple static file servers to JSON APIs to full production servers.

## Starting A Server <a name="Starting"></a>
Express is a Node module, so in order to use it, 
* We will need to import it into our program file. 
* To create a server, the imported express function must be invoked.
```
const express = require('express');
const app = express();
```
On the first line, we import the `Express` library with require. When invoked on the second line, it returns an instance of an Express application. This application can then be used to start a server and specify server behavior.

The purpose of a server is to _listen_ for requests, perform whatever action is required to satisfy the request, and then return a response. In order for our server to start responding, we have to tell the server where to listen for new requests by providing a **port** number argument to a method called `app.listen()`. The server will then listen on the specified port and respond to any requests that come into it.

The second argument is a _callback function_ that will be called once the server is running and ready to receive responses.
```
const PORT = process.env.PORT || 4001;
app.listen(PORT, () => {
  console.log(`Server is listening on port ${PORT}`);
});
```

To actually start your server listening, run the command `node app.js` to run your server in Node.

## Writing Routes <a name="Writing"></a>
Once the Express server is listening, it can respond to any and all requests. But how does it know what to do with these requests? To tell our server how to deal with any given request, we register a series of routes. **Routes** define the _control flow_ for requests based on the `request’s path` and `HTTP verb`.

* The `path` is the part of a request URL `after the hostname and port number`, so in a request to `localhost:4001/monsters`, the path is `/monsters` (in this example, the hostname is ‘localhost’, the port number is ‘4001’).
* The `HTTP verb` is always included in the request, and it is one of a finite number of options used to specify expected functionality. GET, POST, PUT, DELETE, etc.

Express uses `app.get()` to register routes to match `GET` requests. Express routes (including app.get()) usually take **two** arguments, a _path_ (usually a string), and a _callback function_ to handle the request and send a response.

The route above will match any `GET request` to `'/moods'` and call the callback function, passing in two objects as the first two arguments. These objects represent the **request** sent to the server and the **response** that the Express server should eventually send to the client.

If no routes are matched on a client request, the Express server will handle sending a `404 Not Found` response to the client.

```
const moods = [{ mood: 'excited about express!'}, { mood: 'route-tastic!' }];
app.get('/moods', (req, res, next) => {
  // Here we would send back the moods array in response
});
```

## Sending A Response <a name="Sending"></a>
HTTP follows a `one request, one response` cycle. Each client expects exactly one response per request, and each server should only send a single response back to the client per request. 

Express servers send responses using the `.send()` method on the response object. `.send()` will take any input and include it in the response body.

```
const monsters = [{ type: 'werewolf' }, { type: 'hydra' }, { type: 'chupacabra' }];
app.get('/monsters', (req, res, next) => {
  res.send(monsters);
});
```

In this example, a `GET /monsters` request will match the route, Express will call the callback function, and the `res.send()` method will send back an array of spooky monsters.

In addition to `.send()`, `.json()` can be used to explicitly send _JSON-formatted_ responses. `.json()` sends any JavaScript object passed into it.

## Matching Route Paths <a name="Matching"></a>
Express matches routes using both `path` and `HTTP method verb`. **Remember** that the query is not part of the route path.

Express tries to match requests by route, meaning that if we send a request to Express server, Express searches through routes in the order that they are registered in your code. The first one that is matched will be used, and its callback will be called.

For example, if there are two `.get()` routes registered at `/another-route` and `/expressions`. When a `GET /expressions` request arrives to the Express server, it first checks `/another-route`‘s path because it is registered before the `/expressions` route. Because `/another-route` does not match the path, Express moves on to the next registered middleware. Since the route matches the path, the callback is invoked, and it sends a response.

If there are no matching routes registered, or the Express server has not sent a response at the end of all matched routes, it will automatically send back a `404 Not Found` response, meaning that no routes were matched or no response was ultimately sent by the registered routes.

## Route parameters <a name="Route"></a>
Routes become much more powerful when they can be used dynamically. Express servers provide this functionality with named _route parameters_. **Parameters** are route path segments that begin with `:` in their Express route definitions. They act as **wildcards**, matching any text at that path segment. For example `/monsters/:id` will match both `/monsters/1` and `/monsters/45`.

Express parses any parameters, extracts their actual values, and attaches them as an object to the request object: `req.params`. This object’s keys are any parameter names in the route, and each key’s value is the actual value of that field per request.
```
const monsters = { hydra: { height: 3, age: 4 }, dragon: { height: 200, age: 350 } };
// GET /monsters/hydra
app.get('/monsters/:name', (req, res, next) => {
  console.log(req.params) // { name: 'hydra' };
  res.send(monsters[req.params.name]);
});
```
In this code snippet, a `.get()` route is defined to match `/monsters/:name` path. When a GET request arrives for `/monsters/hydra`, the callback is called. Inside the callback, `req.params` is an object with the _key_ `name` and the _value_ `hydra`, which was present in the actual request path. The appropriate monster is retrieved by its name from the `monsters` object and sent back to the client.

## Setting Status Codes <a name="Setting"></a>
Express allows us to set the `status code` on responses before they are sent. Response codes provide information to clients about how their requests were handled.

The `res` object has a `.status()` method to allow us to set the status code, and other methods like `.send()` can be chained from it.
```
const monsterStoreInventory = { fenrirs: 4, banshees: 1, jerseyDevils: 4, krakens: 3 };
app.get('/monsters-inventory/:name', (req, res, next) => {
  const monsterInventory = monsterStoreInventory[req.params.name];
  if (monsterInventory) {
    res.send(monsterInventory);
  } else {
    res.status(404).send('Monster not found');
  }
});
```
All HTTP response status codes are separated into five classes (or categories). The first digit of the status code defines the class of response. The last two digits do not have any class or categorization role. There are five values for the first digit:

* 1xx (Informational): The request was received, continuing process
* 2xx (Successful): The request was successfully received, understood, and accepted
* 3xx (Redirection): Further action needs to be taken in order to complete the request
* 4xx (Client Error): The request contains bad syntax or cannot be fulfilled
* 5xx (Server Error): The server failed to fulfill an apparently valid request

## Matching Longer Paths <a name="MatchingLonger"></a>
Parameters are extremely helpful in making server routes dynamic and able to respond to different inputs. Route parameters will match anything in their specific part of the path, so a route matching `/monsters/:name` would match all the following request paths:
```
/monsters/hydra
/monsters/jörmungandr
/monsters/manticore
/monsters/123
```
In order for a request to match a route path, it must match the entire path, as shown in the diagram to the right. The request arrives for `/expressions/1`. It first tries to match the `/expressions` route, but because it has additional path segments after `/expressions`, it does not match this route and moves on to the next. It matches `/expressions/:id` because `:id` will match any value at that level of the path segment. The route matches, so the Express server calls the callback function, which in turn handles the request and sends a response.

## Other HTTP Methods  <a name="OtherMethods"></a>
**HTTP Protocol** defines a number of different method verbs with many use cases. In addition of GET, there are three other important HTTP methods:  `PUT, POST, and DELETE`. Express provides methods for each one: `app.put(), app.post(), and app.delete()`.
* PUT requests are used for `updating` existing resources. 
* POST is the HTTP method verb used for `creating` new resources. 
* DELETE is the HTTP method verb used to `delete` resources. 

### Using Queries <a name="UsingQueries"></a>
You may have noticed in the previous exercise that our `PUT` route had no information about how to update the specified expression, just the _id_ of which expression to update. It turns out that there was more information in the request in the form of a `query string`. **Query strings** appear at the end of the path in URLs, and they are indicated with a `?` character. For instance, in `/monsters/1?name=chimera&age=1`, the _query string_ is `name=chimera&age=1` and the path is `/monsters/1/`.

**Query strings do not count as part of the route path**. Instead, the Express server parses them into an object and attaches it to the request body as `req.query`. The `key: value` relationship is indicated by the `=` character in a query string, and key-value pairs are separated by `&`. In the above example route, the `req.query` object would be `{ name: 'chimera', age: '1' }`.
```
const monsters = { '1': { name: 'cerberus', age: '4'  } };
// PUT /monsters/1?name=chimera&age=1
app.put('/monsters/:id', (req, res, next) => {
  const monsterUpdates = req.query;
  monsters[req.params.id] = monsterUpdates;
  res.send(monsters[req.params.id]);
});
```

Here, we have a route for updating monsters by ID. When a `PUT /monsters/1?name=chimera&age=1` request arrives, our callback function is called and, we create a `monsterUpdates` variable to store `req.query`. Since `req.params.id` is '1', we replace `monsters['1']`‘s value with `monsterUpdates`. Finally, Express sends back the new `monsters['1']`.

When updating, many servers will send back the updated resource after the updates are applied so that the client has the exact same version of the resource as the server and database.

### Creating An Expression <a name="CreatingExpression"></a>
**POST** is the HTTP method verb used for `creating new resources`. Because POST routes create new data, their paths do not end with a _route parameter_, but instead end with the type of resource to be created.

For example, to create a new monster, a client would make a `POST` request to `/monsters`. The client does not know the `id` of the monster until it is created and sent back by the server, therefore `POST /monsters/:id` doesn’t make sense because a client couldn’t know the unique id of a monster before it exists.

Express uses `.post()` as its method for POST requests. POST requests can use many ways of sending data to create new resources, including query strings.

The HTTP _status code_ for a newly-created resource is **201** Created.

### Deleting Old Expressions <a name="Deleting"></a>
**DELETE** is the HTTP method verb used to `delete` resources. Because DELETE routes delete currently existing data, their paths should usually end with a _route parameter_ to indicate which resource to delete.

Express uses `.delete()` as its method for DELETE requests.

Servers often send a `204 No Content` status code if deletion occurs _without_ error.
