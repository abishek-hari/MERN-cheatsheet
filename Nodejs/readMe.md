### NODE JS

## AGENDA

- NODE AND FEATURES
- ARCHITECTURE
- NODE MODULES
- NPM
- EVENT EMITTER

1. WHAT IS NODE.JS
   Nodejs is javascript runtime environment for executing javascript code
   Highly-scalable, data-intensive and real-time apps
   node is a c++ program includes chrome V8 engine

It provides an event driven, non-blocking (asynchronous) I/O and cross-platform runtime environment for building highly scalable server-side application using JavaScript.
Node.js can be used to build different types of applications such as command line application, web application, real-time chat application, REST API server etc.

2.  FEATURES

- Great for prototyping and agile development
- superfast and highly scalable
- cleaner and more consistent codebase
- large ecosystem of open-source libs

3. How Node Works

- Traditional web server model
  In the traditional web server model, each request is handled by a dedicated thread from the thread pool. If no thread is available in the thread pool at any point of time then the request waits till the next available thread. Dedicated thread executes a particular request and does not return to thread pool until it completes the execution and returns a response.

- node.js model process

Node.js runs in a single process and the application code runs in a single thread. All the user requests will be handled by a single thread and will be performed asynchronously. So, this single thread doesn't have to wait for the request to complete and is free to handle the next request. When asynchronous I/O work completes then it processes the request further and sends the response.

An event loop is constantly watching for the events to be raised for an asynchronous job and executing callback function when the job completes. Internally, Node.js uses libev for the event loop which in turn uses internal C++ thread pool to provide asynchronous I/O.

Blocking-sync/Non-blocking-Async
In node you have a single thread to access multiple requests

- Thread
  when we receive a request on the server a thread is allocated to handle that request

4. What is REPL
   Node.js comes with virtual environment called REPL ( Node shell). REPL stands for Read-Eval-Print-Loop. It is a quick and easy way to test simple Node.js/JavaScript code.

5. MODULES IN NODE.JS
   A module is essentially a reusable block of code that can be used to perform a specific set of tasks or provide a specific functionality
   The primary purpose of using modules in Node.js is to help organize code into smaller, more manageable pieces

Module.exports:
module.exports is a special object in NodeJS that allows you to export functions, objects, or values from a module, so that other modules can access and use them.

```js
function myFunction() {
  console.log("Hello from myFunction!");
}

module.exports = myFunction;
```

6. NODE.JS includes Three types of Modules

- Core Modules (Built-in) These are modules included in Node by default
- Local Modules
- External Modules

* CORE MODULES

  - OS (It provides the information about the operating system)
  - PATH (Provides utlity functions for working with files)
  - FS (File systems operation like reading and writing files)
  - HTTP (creates HTTP servers)

* LOCAL MODULES

```js
// In info.js
const info = {
  info: function (info) {
    console.log("Info: " + info);
  },
};

// In app.js

var myInfo = require("./info.js");
myInfo.info("Node.js started");
```

- EXTERNAL MODULES
  These are modules created by other developers which are not included by default. So you need to install them first before using them.

7. NPM
   Node Package Manager (NPM) is a command line tool that installs, updates or uninstalls Node.js packages in your application. It is also an online repository for open-source Node.js packages.

8. EVENT EMITTER

<!-- NODE BASIC QUESTIONS -->

1. Is Node.js single-threaded?

   Yes, Node.js is single-threaded by default. However, it utilizes event-driven architecture and non-blocking I/O operations to handle multiple concurrent requests efficiently, enabling scalability and high performance in applications.

2. What kind of API function is supported by Node.js?
   There are two types of API functions supported by Node.js:

   Synchronous: These API functions are used for blocking code.
   Asynchronous: These API functions are used for non-blocking code.

3. What is middleware?
   Middleware is the function that works between the request and the response cycle. Middleware gets executed after the server receives the request and before the controller sends the response.

4. what is concurrency?
   Concurrency is an essential feature of Node. js that enables it to handle large numbers of I/O operations simultaneously, without blocking the execution thread. This concurrency model allows Node. js to handle many requests concurrently, resulting in improved application performance.

5. What is event-driven programming in Node.js?
   Event-driven programming is a paradigm where the flow of the program is determined by events such as user actions (clicks, key presses) or messages from other programs or threads.The basic components of an Event-Driven Program are:

   A callback function ( called an event handler) is called when an event is triggered.
   An event loop that listens for event triggers and calls the corresponding event handler for that event.

Eg:
When a user adds an item to their cart, an "item added to cart" event is triggered.
The event is captured by the e-commerce system, which updates the cart total and sends a response to the user interface.

Event-driven architecture (EDA) is an architectural style used in software development and design to build scalable, loosely coupled, and responsive systems. This architecture is often used in systems that need to handle a large number of asynchronous events efficiently, such as web servers.

Event Sources: User actions (e.g., adding items to cart, placing an order, updating account details), external systems (e.g., payment gateways, inventory management systems).
Event Processing: The e-commerce system processes events like "item added to cart," "order placed," or "payment received."
Event Handlers: Based on the events, the system triggers actions such as updating the cart total, updating inventory levels, or sending order confirmation emails.
Asynchronous Communication: Events are communicated asynchronously, allowing the system to handle multiple events concurrently.

EDA is more about the high-level design principles and concepts, while EDP is about the actual coding practices and techniques used to implement those principles.

runtime for js - Node.js , python - Cpython , Java - JVM , C# - CLR
Runtime environment is for memory management and for converting High level languages to lower level languages.
(Machine or computer understandable)
Frameworks are like wrapper over the runtime. Frameworks provides more features over the runtime

02 - How node is a runtime environment on server side? what is v8?
Browsers execute javascript on the client side, and similarly, Node.js executes javascript on the server side.
v8 is a javascript engine for the javascript language.

03 - what is the difference between Runtime environment & Framework?
Runtime Environment: Primarily focuses on providing the necessary infrastructure for code execution, including services like memory management and I/O operations.
Framework: primarily focuses on simplifying the development process by offering a structured set of tools, libraries, and best practices.

04 - what is difference between Node.js & Express.js
Node.js is a runtime environment that allows the execution of the js code in server side
express.js is a framework built on the top of node.js
It is designed to simplifiy the process of building web applications and APIs by providing a set of feature like simple routing system, middleware support etc.

05 - client vs server side

user -----> request ---> client side ----> server-side -----> Database server
---------------------------(React.js)----- (Node + express)

Environment Location - Runs on the user web browser = Runs on the server.
primary Languages - HTML, CSS, JS = Javascript
Document/window/Event objects are available in browser and not in the server
request/response/server/database object are not in browser but are present in server.
Respossibilites - Hanldes UI display, interactions, and client-side logic = Hanldes business logic, data storage, authentication and authorization.

# Main Features of Node.js

01 - What are the & Main Features of Node.js

- Single Threaded
- Asynchronous
- Event Driven
- V8 Javascript Engine
- Cross-platform
- NPM
- Real-Time Capabilities

02 - What is Single Threaded programming
It works synchronously when there a multiple task each task wait for the previous task to completed and the move to the next task.
It is executed one task at a time.

03 - What is synchronous programming?
synchronous code executes one task at a time, in a sequennce. Each task must wait for the previous one to complete before moving on to the next.

04 - What is Multi thread programming?

05 - What is Asynchronous programming?
Asynchronous code execution allows to execution next instructions immediately without waiting for the previous ones to complete.. It enables non-blocking operations,It means that the program can continue executing code while certain tasks are in progress.

whenever a task is completed a event is raised
06 - what are events , Even Emmitter, Event Queue, Event loop & Event Driven?

event emiiters generate events and all generated events are stored in the event Queue and the event Handler (Event Listener) will perform the code.
event loop is the one which dequeue the events.

Event: Signals that something has happened in a program.
Event Emitter: Create or emit events
Event Queue: Events emmited queued(stored) in event queue.
Event Hanlder(Event Listener):Function that responds to specific events.
Event loop: The event loop picks up event from the event queue and executes them in the order they were added.
Event Driven Architeture: It means operations in Node are drive or based by events.

07 - Main features & Adavtages of Node.js

==== FEATURE =========== ADVANTAGES =============================
Asynchronous ---> Enables handling multiple concurrent requests & non blocking execution of thread.
V8 js Engine ---> Built on the V8 js Engine from Goggle Chrome, Node.js executes code fast
Event Driven Architecture ---> Efficient handling events, Great for real time applications like chat applications, gaming applications(using web sockets) where bidirectional communication is required.
Cross-Platform ---> Supports deployment on various operating systems, enhancing flexibility.
Javascript ---> Coding in Js language therefore no need to learn new language.
Suitable for building scalable applications that can handle incresed loads.

08 - What are the disadvantages of node? When to use and when not to use Node?
For CPU-Intensive Takes you no need to use Node

<!-- 03 - PROJECT SETUP & MODULES -->

01 - How to setup node.js project
02 - What is NPM? What is the role of node_modules folder?
03 - What is the role of package.json file in Node?
04 - What are Modules in Node?
05 - How many ways are there to Export a module?
06 - What will happen if you dont export the module?
07 - How to import single and multiple functions from a module?
08 - What is module wrapper function?
09 - What are the Types of modules in Node?

01 - How to setup node.js project
6 steps for setting up Node.js in VScode

- Download node and install the node.js
- create a new folder & open it on VScode
- open terminal in VScode and run `npm init -y`
- create a new JS file within your project folder
- Run your node application using the node app.js in the terminal

02 - What is NPM? What is the role of node_modules folder?

- NPM - It is used to manage the dependencies for your Node project.
- node_modules - this folder contains all the dependencies of the node project.

03 - What is the role of package.json file in Node?
The package.json file contains project metadata(information about the project). For example project name, version, author, license etc.

04 - What are Modules in Node?
A module is essentially a reusable block of code that can be used to perform a specific set of tasks or provide a specific functionality
The primary purpose of using modules in Node.js is to help organize code into smaller, more manageable pieces.

Difference:
A module is a broader concept that encapsulates functionality, while a function is a specific set of instructions within that module.
Module can contain multiple functions variables

05 - How many ways are there to Export a module?

```js
// to export func , var and obj you can use module.exports
function sayHello() {
  console.log("Hello");
}
module.exports.sayHello = sayHello;

// another way
exports.sayHello = function () {
  console.log("Hello");
};
```

06 - What will happen if you dont export the module?
If you don't export the module, then the module functions will not be avilable outside the module.

07 - How to import single and multiple functions from a module?

```js
// we can import using 2 ways
const module1 = require("./module1");

// To import single function
module1("hello");

// To multiple function (we have to provide the function)
module1.sayHello("Happy");
module1.sayHello("Happy");
```

08 - What is module wrapper function?
In Node.js, each module is wrapped in a function called the "module wrapper function" before it is executed.

```js
// Wrapper function created by node
(function (exports, require, module, __filename, __dirname) {
  const message = "Interview Happy";

  console.log(message);
});
```

09 - What are the Types of modules in Node?

- Core Modules (Built-in) These are modules included in Node by default
- Local Modules (These are user defined modules)
- External Modules (These are external packages or libraries created by the community and provide additional functinality.)

<!-- 4 - Top built in modules -->

01 - what are the Top 5 built in modules commonly used in node projects?
02 - Explain the role of fs module? Name some function of it
03 - Explain the role of path module? Name some functions of it?
04 - Explain the role of os module? Name some functions of it?
05 - Explain the role of events module? How to handle events in Node?
06 - What are Event Arguments?
07 - WHat is the difference between a function and an Event?
08 - WHat is the role of http module in node?
09 - What is the role createServer() method of http module?

01 - what are the Top 5 built in modules commonly used in node projects?

- fs
- path
- os
- events
- http

02 - Explain the role of fs module? Name some function of it

- fs module is node provides a set of methods for interacting with the file system.

```js
import fs from "fs";

// Reading the contents of a file asynchronously
fs.readFile("fs.txt", "utf8", (err, data) => {
  if (err) {
    return;
  }
  console.log("File contents:", data);
}); // first is the path, second is the module and third is the data

// writing to a file asynchronously
const contentToWrite = "some content";
fs.writeFile("fs.txt", contentToWrite, "utf8", (err, data) => {
  if (err) {
    return;
  }
  console.log("File contents:", data);
}); // first is the path, second is the module and third is the data
```

7 Main functions of fs module:

- fs.readFile() = Reads the content of the file specfied
- fs.WriteFile() = Write data to the specified file, creating the file if it does not exist.
- fs.appendFile() = Appends data to a file. If the file does not exist, it is created.
- fs.unlink() = Deletes the specified file.
- fs.readdir() = Reads the contents of a directiry.
- fs.mkdir() = creates a new directory.
- fs.rmdir() = removes the specified directory.

03 - Explain the role of path module? Name some functions of it?

- Path module provides utilites for joining, resolving, parsing, formatting, normalizing, and manipulating paths

```js
import path form 'path';

// joining path segemnts together
const fullPath = path.join('/docs', 'file.txt');
console.log(fullPath);
// Output : /docs/file.txt

// parsing a path into an object with its components
const parsedPath = Path.parse('/docs/file.txt');
console.log(parsedPath)
// It will convert it into object
// output: {root:'/', dir:'/docs', base:'file.txt'...}

// Resolving the absolute path
const absolutePath = path.resolve('folder', 'file.txt')

// Getting the directory name of a path
const absolutePath = path.dirname('/folder/file.txt')

// Getting the file extension of a path
const absolutePath = path.extname('/folder/file.txt')
```

04 - Explain the role of os module? Name some functions of it?

- The os module in Node.js provides a set of methods for interacting with the operating system.
- OS can be used by developers for building cross-platform applications or performing system-related tasks in Node.js applications.

```js
import os form 'os'
// Get platform Information
console.log(os.type())

// get current user Information
console.log(os.userInfo())

// Get memory Information in bytes
console.log(os.totalmem())
console.log(os.freemem())

```

05 - Explain the role of events module? How to handle events in Node?
Event: Signals that something has happened in a program.
Event Emitter: Create or emit events
Event Queue: Events emmited queued(stored) in event queue.
Event Hanlder(Event Listener):Function that responds to specific events.
Event loop: The event loop picks up event from the event queue and executes them in the order they were added.
Event Driven Architeture: It means operations in Node are drive or based by events.

```js
import EventEmitter from "events";

// create an instance of eventEmitter class
const myEmitter = new EventEmitter();

// Register an event listener(eventName)
myEmitter.on("eventName", () => {
  console.log("Events Occurred");
});

// Emit the event
myEmitter.emit("eventNAme");

// output: Event occurred
```

06 - What are Event Arguments?
Event arguments refer to the additional information or data that can be passed along with an emmitted event.

```js
import EventEmitter from "events";

// create an instance of eventEmitter class
const myEmitter = new EventEmitter();

// Register an event listener(eventName)
myEmitter.on("eventName", (arg1, arg2) => {
  console.log("Events Occurred": arg1, arg2);
});

// Emit the event
myEmitter.emit("eventNAme", "arg1", "arg2");

// output: Event occurred
```

07 - What is the difference between a function and an Event?

- A function is a reusable piece of code that performs a specific task when invoked or called.
- Events represent actions that can be observed and responded to. Events will call functions internally.

08 - What is the role of http module in node?
The http module can create an HTTP server that listens to server ports and gives a response back to the client.

09 - What is the role createServer() method of http module?
The createServer() method of the http moudle is Node.js is used to create an HTTP server.

```js
import http from "http";

// create an HTTP sever
const server = http.createServer((req, res) => {
  // handling incoming HTTP requests here
  res.end("Hello, World");
});

// set port on which server will listen incoming requests
const port = 3000;

// start the server and listen on the specified port
server.listen(port, () => {
  console.log(`server is running in port${port}`);
});
```
