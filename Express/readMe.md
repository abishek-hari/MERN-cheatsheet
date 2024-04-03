### EXPRESS

01 - Express Basics
02 - MiddleWare
03 - Types of MiddleWare's
04 - Routing - 1
05 - Routing - 2
06 - Template Engine

01 - Rest Api Basics
02 - HTTP Methods & status codes
03 - CORS, serialization, Deserialization, others
04 - Authentication & Authorization
05 - Error Handling & Debugging

<!-- BASICS -->

01 - What are the advantages of using Express.js with Node.js?
02 - How do you install Express.js in Node.js project?
03 - How to create an HTTP server using Express.js?
04 - How do you create and start Express.js application?

01 - What are the advantages of using Express.js with Node.js?

- Simplified web development
  (Express.js provides a lightweight framework that simplifies the process of building web applications in Node.js)
- Middleware support
  (Easy intergation of middleware functions into applications request response cycle.)
- Fexlible Routing system
  (Defining routes for handling different HTTP methods (GET, POST, PUT & DELETE, etc.) and URL patterns is easy)
- Template Engine Integration
  It helps us to create dynamic html content on the server side

02 - How do you install Express.js in Node.js project?
open the terminal and install `npm install express`

03 - How to create an HTTP server using Express.js?

```js
import express from "express";

const app = express();

const PORT = 3000;

app.listen(PORT, () => {
  console.log(`Running on server ${PORT}`);
});
```

04 - How do you create and start Express.js application?

```js
import express from "express";

const app = express();

const PORT = 3000;

app.get("/", (req, res) => {
  res("HEllO");
});

app.listen(PORT, () => {
  console.log(`Running on server ${PORT}`);
});
```

<!-- MIDDLEWARE -->

01 - What is Middleware in Express.js and When to use them?
02 - How do you implement middleware in Express.js
03 - What is the purpose of the app.use() function in Express.js?
04 - What is the purpose of next parameter in Express.js?
05 - How to use middleware globally for a specific route?
06 - What is request pipeline in Express?

01 - What is Middleware in Express.js and When to use them?
A middleware is a function that handles HTTP request, perform's operations, and passes control to the next middleware.

02 - How do you implement middleware in Express.js

```js
import express from "express";
const app = express();

const myMiddleware = (req, res, next) => {
  res.send("hello");
  next(); // call the next middleware function.
};
// use app.use() to mount myMiddleware globally, meaning it will be executed for every incoming request to the application.

app.use(myMiddleware);

const PORT = 3000;
app.listen(PORT, () => {
  console.log(`Running on server ${PORT}`);
});
```

03 - What is the purpose of the app.use() function in Express.js?
The app.use() method is used to execute(mount) middleware functions globally.

04 - What is the purpose of next parameter in Express.js?
The next parameter is a callback function which is used to pass control to the next middleware function in the stack.

05 - How to use middleware globally for a specific route?
Use app.use('speificroute', middleware) to use middleware globally for a specific routes

```js
import express from "express";
const app = express();

const myMiddleware = (req, res, next) => {
  res.send("hello");
  next(); // call the next middleware function.
};

// use middleware globally for specific routes
app.use("/example", myMiddleware);

const PORT = 3000;
app.listen(PORT, () => {
  console.log(`Running on server ${PORT}`);
});
```

06 - What is request pipeline in Express?
The request pipleline is a series of middleware functions that hanlde incoming HTTP requests and pass control to the next function.

<!-- TYPES OF MIDDLEWARE'S -->

01 - What are the type of middleware's in Express.js?
02 - What is the difference btw application-level & route-level middleware?
03 - what is error handling middleware and how to implement it?
04 - If you have 5 middleware then in which middleware you will do the error handling?
05 - what is built in middleware's? How to serve static files from Express.js
06 - what are third-party middleware's?
07 - can you summarize all the type of middleware's
08 - what are the adavantages of using middleware in Express.js?

01 - What are the type of middleware's in Express.js?
5 Types of Middleware

- Application-level middleware
- Router-level middleware
- Error-handling middleware
- Built-in middleware
- Third-party middleware

02 - What is the difference btw application-level & route-level middleware?

```js
// Application-level middleware applies globally to all incoming requests in the entire Express.js application.
import express from "express";
const app = express();

const myMiddleware = (req, res, next) => {
  res.send("hello");
  next(); // call the next middleware function.
};

app.use(myMiddleware);

const PORT = 3000;
app.listen(PORT, () => {
  console.log(`Running on server ${PORT}`);
});

// Router-level middleware applies only to specific routes, not for all incoming requests.
import express from "express";
const app = express();

const myMiddleware = (req, res, next) => {
  res.send("hello");
  next(); // call the next middleware function.
};

// use middleware globally for specific routes
app.use("/example", myMiddleware);

const PORT = 3000;
app.listen(PORT, () => {
  console.log(`Running on server ${PORT}`);
});
```

03 - what is error handling middleware and how to implement it?
Error handling middleware is a special kind of middleware used to manage errors happening while handling incoming requests.

```js
import express from "express";
const app = express();

app.use((req, res, next) => {
  // simulate an Error
  next(Error("An error occured"));
});

// Error handling middleware
app.use((err, req, res, next) => {
  console.error(err.stack);
  res.status(500).send("Something broke!");
});

const PORT = 3000;
app.listen(PORT, () => {
  console.log(`Running on server ${PORT}`);
});
```

04 - If you have 5 middleware then in which middleware you will do the error handling?
In case of multiple middleware, error handling middleware should be defined at last because when an error occurs, Express will search for the next error-handling middleware skipping any regular middleware or route handlers.

```js
app.use((err, req, res, next) => {
  console.error(err.stack);
  res.status(500).send("Something broke!");
});
```

05 - what is built in middleware's? How to serve static files from Express.js
Built-in middleware are build in functions inside framework which provides common functionalities.
express.static() middleware is used for serving static files.
some common built-in middleware:
express.json()
express.urlencoded()
express.static()

```js
import express from "express";
const app = express();

app.use(express.static("public"));
```

06 - what are third-party middleware's?
Third-party middleware are modules developed by third-party developers

```js
import helmet from "helmet";
import cors from "cors";
import bodyParser from "body-parser";

const app = express();
app.use(helmet());
```

<!--  -->

08 - what are the adavantages of using middleware in Express.js?

<!-- ROUTING - 1 -->

CLIENT -> MIDDLEWARE -> ROUTING -> --[ORDERS, PRODUCTS, PAYMENTS]

01 what is Routing in Express.js?
02 - What is the difference between Middleware and rounting
03 - How to implement routing? How do you define routes in Express.js
04 - How to handle Routing in real applications

01 what is Routing in Express.js?
Routing is the process of directing incoming HTTP requests to the appropriate handler functions based on the requests method(GET POST) and the URL path.

02 - What is the difference between Middleware and rounting

1. middleware are function
   middleware will perform somelogic

   - perform some actions
   - end the request-response cycle
   - call the next middleware function

2. Routing is a process
   Routing is the process of directing incoming HTTP requests to the appropriate handler functions based on the requests method(GET< POST) and the URL path.

03 - How to implement routing? How do you define routes in Express.js
Routes are defined using the app.METHOD() and app is an instance of express application.

```js
import express from "express";
const app = express();

app.get("/", (req, res) => {
  res.send("Interview");
});
```

04 - How to handle Routing in real applications

```js
import express from "express";
const app = express();
// middleware
// controllers
import orderRoute from "./controllers/ordersRoute";

app.get("/", orderRoute);
```

05 - What are Route Hanlders
Route hanlder is the second argument passed to app.get() or other method
router handler function is used to process the request and response.

```js
import express from "express";
const app = express();

app.get("/", (req, res) => {
  res.send("Interview");
});
```

06 - What are Route parameters?
Route parameter allow you to capture dynamic values from the URL paths.
Route parameters can be accessed by using req.params object.

```js
import express from "express";
const app = express();

app.get("/users/:userID", (req, res) => {
  res.send("Interview");
});
```

<!-- TEMPLATE ENGINE -->

Template engines are libraries that enables developers to generate dynamic HTML content by combining satic HTML template with data.

some of the Template Engines Libraries
EJS(Embeded javascript), PUG , Hanldebars

how to implement

- install ejs
- create a folder views & create a file index.ejs
- create a server.js
- we use set method to set the view engine to EJS

```js
import express from "express";
const app = express();

app.set("view engine", "ejs");

// set the views directory
app.set("views", path.join(__dirname, "views"));

// route to render the index.ejs template
app.get("/", () => {
  res.render("index", { title: "Node.js with EJS" });
});
```

<!-- REST API -->

01 - What is REST & RESTFUL api
02 - what are HTTP request and reponse structure in UI and REST API
03 - What are TOP % REST guideline and the advatages of them
04 - What is the differnce between REST API & SOAP API

01 - What is REST & RESTFUL api

enter the application url ---> request(client side) ---> request(server side)(REST API) --> DATABASE
REST (Representational state Transfer) is an architectural style for designing networked applications
(REST is a set of guidelines for creating API's)

RESTful API is a service which follow REST principles/guidlines.

02 - What are the HTTP Request and response structure in UI and REST API
POST | HTTP | HOST | HEADER & CONTENT_TYPE

HTTP REQUEST - An HTTP (HYPERTEXT TRANSFER PROTOCOL) request is a message sent by a client to a server, requesting a pariticular action or resource.
It contains HTTP Action (GET< POST), URL, request Body , request Header.

An HTTP response is a message sent by a server back to the client in response to an HTTP request.
It includes status code, content type, content.

03 - What are TOP 5 REST guideline and the advatages of them

- separation of client and server
- stateless
- Uniform interface
- cacheable
- Layered system

04 - What is the differnce between REST API & SOAP API

Architecture :

- REST is an architectural style
- SOAP (simple object Acess Protocol)

Protocol:
uses HTTP OR HTTPS
can use various protocols(HTTP< SMTP< etc.,)

Message Format:

- Uses lightweight formats like JSON, XML
- Typically uses XML

State:
Stateless

- can be staeful or stateless

Error Hanlding:
Relies on HTTP status codes.
Defines its own fault mechanism.

Performance:
Generally lightweight and faster
can be slower due to XML processing.

CORS:
CORS(Cross-Origin Resource sharing) is a security feature implemented in web browsers that restricts web pages or scripts from making requests to a different domain than the one that served the web page.

<!-- AUTHENTICATION AND AUTHORIZATION -->

01 -
Authentication is the process of verifying the identity of a user by validating their credentials such as username and password.

Authorization is the process of allowing an authenticated user acess to resources. Autenctication is always precedes to Authorization.

02 - Types of Authentication

- Basic(username and password) Authentication
- API key Authentication
- Token-Based Authentication(JWT)
- Multi-factor Authentication(MFA)
- Certificate-based Authentication

Basic Authentication:
In basic Authentication, The user passes their credentials on a post request. At the node REST API end, credentials are verified, and response is sent back
The disadvantages of it is, Basic Authentication sends credentials in palin text over the next, so it is not considered a secure method of authentication.

What are the security risks associated with storing passwords in plain text in Node.js

- Unauthorized Acess: Storing passwords in plain text means that anyone with acess to the storage location, such as a database or configuration file, can easily read and extract passwords.
- compromise of other Accounts: Many users tend to reuse password accross multiple accounts, allowing attckers to access to multiple accounts.

03 - What is the role of hashing and salt in secure passwords?
Hashing: Hashing is a process of converting a password into a fixed size string of characters using a mathematical algorithm.

```js
const hashedPassword = await bcrypt.hash(password, 10);
const isPasswordvalid = await bcrypt.compare(password, user.password);
```

API Key AUthentication:
IN API key authentication, the API owner will share an API key with the users ad this key will authenticate the users of that API.
The disadvantages of it is , API keys can be shared or stolen.

What is Token based and JWT authentication?
This has 8 process

- POST:{username, password}
- Authentication & create JWT token
- return response {JWT token}
- store jwt token at local storage
- request data {jwt token:header}
- validate token signature
- send data
- Dispplay data on the browser

```js
// In login route
const token = jwt.sign({ id: user._id }, "secret");
res.json({ token, userId: user._id, username });

export const verifyToken = (req, res, next) => {
  const token = req.headers.authorization;
  if (token) {
    jwt.verify(token, "secret", (err) => {
      if (err) return res.sendStatus(403);
      next();
    });
  } else {
    res.sendStatus(401);
  }
};
```

 <!-- DEBUGGING NODE.JS APPLICATIONS -->

console.log()
debugger statement
chrome devTools

<!-- JWT -->

What is JWT?
JWT is a compact, URL-safe means of representing claims to be transferred between two parties.

How does JWT work?
JWTs are composed of three parts: a header, a payload, and a signature. These parts are separated by dots.

What are the components of a JWT?
Header: Contains metadata about the type of token and the signing algorithm used.
Payload: Contains the claims. Claims are statements about an entity and additional data.
Signature: Used to verify that the sender of the JWT is who it says it is and to ensure that the message wasn't changed along the way.

What are the use cases for JWT?
Authorization: JWTs are commonly used for user authentication and authorization in web applications.
Information Exchange: JWTs can be used to securely transmit information between parties.

How are JWTs validated?
The signature in the JWT is used to validate the token. The recipient of the JWT can verify the signature using the secret key (in the case of HMAC algorithms) or the public key (in the case of RSA algorithms).

What are the advantages of using JWT?
Stateless: JWTs are stateless, meaning that servers don't need to store session information.
Scalability: JWTs can improve the scalability of applications by reducing the load on servers.

What are the disadvantages of using JWT?
Size: JWTs can be larger than other authentication tokens, especially when including large amounts of data in the payload.
Security: JWTs can be susceptible to some attacks, such as replay attacks if not used properly.

How are JWTs secured?
JWTs can be secured by using strong cryptographic algorithms for signing and verifying the tokens. It's also important to keep the secret or public key used for signing the tokens secure.
