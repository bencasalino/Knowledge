## Express:

Express is a Node module, so in order to use it, we will need to import it into our program file. To create a server, the imported express function must be invoked.

```
const express = require('express');
const app = express();
```

On the first line, we import the Express library with require. When invoked on the second line, it returns an instance of an Express application. This application can then be used to start a server and specify server behavior.

The purpose of a server is to listen for requests, perform whatever action is required to satisfy the request, and then return a response.

In order for our server to start responding, we have to tell the server where to listen for new requests by providing a port number argument to a method called **app.listen()**. The server will then listen on the specified port and respond to any requests that come into it.

The second argument is a callback function that will be called once the server is running and ready to receive responses.

```
const PORT = 4001;
app.listen(PORT, () => {
  console.log(`Server is listening on port ${PORT}`);
});
```

Simple Express Example:

```
// Import the express library here
const express = require('express');

// Instantiate the app here
const app = express();

// define the port
const PORT = process.env.PORT || 4001;

// Invoke the app's `.listen()` method below:
app.listen(PORT, () => {
  console.log(`Server is listening on port ${PORT}`);
});
```

# Routes with Express

Once the Express server is listening, it can respond to any and all requests.
But how does it know what to do with these requests?
To tell our server how to deal with any given request, we register a series of routes.

Routes define the control flow for requests based on the request's path and HTTP verb.

Example Route:

For example, if your server receives a GET request at '/monsters', we will use a route to define the appropriate functionality for that HTTP verb (GET) and path (/monsters).

The HTTP verb is always included in the request, and it is one of a finite number of options used to specify expected functionality.

Example: GET requests are used for retrieving resources from a server.

Express uses app.get() to register routes to match GET requests.

Express routes (including app.get()) usually take two arguments, a path (usually a string), and a callback function to handle the request and send a response.

```
const moods = [{ mood: 'excited about express!'}, { mood: 'route-tastic!' }];
app.get('/moods', (req, res, next) => {
  // Here we would send back the moods array in response
});
```

The route above will match any GET request to '/moods' and call the callback function, passing in two objects as the first two arguments. These objects represent the request sent to the server and the response that the Express server should eventually send to the client.

If no routes are matched on a client request, the Express server will handle sending a 404 Not Found response to the client.

Sending A Response
HTTP follows a one request-one response cycle. Each client expects exactly one response per request, and each server should only send a single response back to the client per request.

Express servers send responses using the .send() method on the response object.
.send() will take any input and include it in the response body.

```
const monsters = [{ type: 'werewolf' }, { type: 'hydra' }, { type: 'chupacabra' }];
app.get('/monsters', (req, res, next) => {
  res.send(monsters);
});
```

In this example, a GET /monsters request will match the route, Express will call the callback function, and the res.send() method will send back an array of spooky monsters.

Note:
In addition to .send(), .json() can be used to explicitly send JSON-formatted responses. .json() sends any JavaScript object passed into it.

Getting A Single Expression
Routes become much more powerful when they can be used dynamically. Express servers provide this functionality with named route parameters. Parameters are route path segments that begin with : in their Express route definitions. They act as wildcards, matching any text at that path segment. For example /monsters/:id will match both/monsters/1 and /monsters/45.

Express parses any parameters, extracts their actual values, and attaches them as an object to the request object: req.params. This object's keys are any parameter names in the route, and each key's value is the actual value of that field per request.

const monsters = { hydra: { height: 3, age: 4 }, dragon: { height: 200, age: 350 } };
// GET /monsters/hydra
app.get('/monsters/:name', (req, res, next) => {
console.log(req.params) // { name: 'hydra' };
res.send(monsters[req.params.name]);
});
In this code snippet, a .get() route is defined to match /monsters/:name path. When a GET request arrives for /monsters/hydra, the callback is called. Inside the callback, req.params is an object with the key name and the value hydra, which was present in the actual request path. The appropriate monster is retrieved by its name from the monsters object and sent back the the client.
