---
title: Node.js Modules
hide:
  - tags

tags:
  - Node.js Modules
  - Core Modules
  - Custom Modules
  - EventEmitter
  - Child Threads

---

# Node.js Modules

---

## Node.js Modules

Node.js is a runtime environment that allows developers to execute JavaScript code on the server-side. Modules in
Node.js are a fundamental part of organizing and structuring code. They are containers for encapsulating code,
variables, and functions, making it easier to manage and reuse code in a scalable and maintainable manner.

### Why Use Modules in Node.js?

Using modules in Node.js provides several benefits, including:

1. **Code Reusability:** Modules allow you to encapsulate code and reuse it across different parts of your application
   or even in multiple projects.

2. **Maintainability:** Modules help in organizing code into smaller, manageable pieces, making it easier to debug and
   maintain.

3. **Encapsulation:** Modules encapsulate variables and functions, preventing them from polluting the global scope and
   avoiding naming conflicts.

4. **Dependency Management:** Modules help in managing dependencies between different parts of your application by
   importing and exporting functions and variables.

### Types of Node.js Modules

Node.js supports two types of modules:

1. **Core Modules:** These are built-in modules that come with Node.js and provide essential functionality. You can use
   them without installing any additional packages. Examples include the `fs` module for file system operations and
   the `http` module for creating web servers.

2. **Custom Modules:** These are modules created by developers to organize their code. Custom modules can be further
   divided into two subtypes:
    - **Local Modules:** These modules are created within your project and can be used to encapsulate related code. You
      can create a local module by defining your functions and variables in separate files.
    - **Third-party Modules:** These are modules developed by the community and can be installed via Node Package
      Manager (NPM). They provide a wide range of functionality, from handling authentication to database connections.

### Creating and Using Modules

To create and use modules in Node.js, follow these steps:

1. **Create a Module:** In a separate `.js` file, define your variables and functions. For example, a file
   named `myModule.js`:

   ```javascript
   // myModule.js
   const myVariable = 'Hello, World!';
   
   function sayHello() {
       console.log(myVariable);
   }
   
   module.exports = {
       sayHello
   };
   ```

2. **Import a Module:** In your main application file, import the module using `require()`:

   ```javascript
   // app.js
   const myModule = require('./myModule');
   
   myModule.sayHello(); // This will print "Hello, World!" to the console.
   ```

3. **Use the Module:** You can now use the functions and variables exported from the module in your application.

Node.js modules are essential for structuring, organizing, and reusing code in Node.js applications. They help in
maintaining clean, modular, and maintainable code, making development more efficient and less error-prone. Whether using
core modules or creating custom modules, understanding how to work with modules is crucial for Node.js developers.



---

## Node.js Modules

Node.js is a runtime environment for executing JavaScript code on the server-side. Modules in Node.js are a way to
encapsulate code, variables, and functions, making it easier to organize, reuse, and maintain code in a scalable and
modular fashion. Node.js supports two types of modules: Core Modules and Custom Modules.

### Core Modules

Core modules are built-in modules that come with Node.js. They provide essential functionality and can be used without
installing any additional packages. Some commonly used core modules include:

Certainly! Here are some Node.js core modules with examples of how to use them:

#### 1. `fs` (File System)

- Example: Reading a file asynchronously using `fs.readFile()`:

```javascript
const fs = require('fs');

fs.readFile('example.txt', 'utf8', (err, data) => {
    if (err) {
        console.error(err);
        return;
    }
    console.log(data);
});
```

#### 2. `http` (HTTP)

- Example: Creating a simple HTTP server using `http.createServer()`:

```javascript
const http = require('http');

const server = http.createServer((req, res) => {
    res.writeHead(200, {'Content-Type': 'text/plain'});
    res.end('Hello, World!\n');
});

const PORT = 3000;
server.listen(PORT, () => {
    console.log(`Server listening on port ${PORT}`);
});
```

#### 3. `path` (Path)

- Example: Joining and resolving paths using `path.join()` and `path.resolve()`:

```javascript
const path = require('path');

const basePath = '/root';
const relativePath = 'documents';
const fullPath = path.join(basePath, relativePath);
console.log(fullPath);

const absolutePath = path.resolve(basePath, relativePath);
console.log(absolutePath);
```

#### 4. `util` (Utilities)

- Example: Using `util.inspect()` to inspect objects:

```javascript
const util = require('util');

const myObject = {
    name: 'John',
    age: 30,
    hobbies: ['reading', 'coding']
};

console.log(util.inspect(myObject, {depth: null}));
```

#### 5. `os` (Operating System)

- Example: Getting information about the operating system using `os.platform()` and `os.totalmem()`:

```javascript
const os = require('os');

console.log(`Operating System: ${os.platform()}`);
console.log(`Total Memory: ${os.totalmem()} bytes`);
```

These examples demonstrate how to use some of the Node.js core modules to perform common tasks like file reading,
creating an HTTP server, working with paths, inspecting objects, and retrieving information about the operating system.
You can explore more features and methods provided by these core modules in the Node.js documentation to suit your
specific needs.

#### 6. `events` (Event Emitter)

- Example: Creating a custom event emitter and listening to events:

```javascript
const EventEmitter = require('events');

class MyEmitter extends EventEmitter {
}

const myEmitter = new MyEmitter();

myEmitter.on('customEvent', (arg1, arg2) => {
    console.log('Custom event received:', arg1, arg2);
});

myEmitter.emit('customEvent', 'Hello', 'World');
```

#### 7. `crypto` (Cryptographic)

- Example: Creating an SHA-256 hash using `crypto.createHash()`:

```javascript
const crypto = require('crypto');

const data = 'Hello, World!';
const hash = crypto.createHash('sha256').update(data).digest('hex');

console.log('SHA-256 Hash:', hash);
```

#### 8. `url` (URL)

- Example: Parsing and formatting URLs using `url.parse()` and `url.format()`:

```javascript
const url = require('url');

const urlString = 'https://www.example.com:8080/path?query=parameter#fragment';
const parsedUrl = url.parse(urlString);

console.log('Parsed URL:', parsedUrl);
console.log('Formatted URL:', url.format(parsedUrl));
```

#### 9. `querystring` (Query String)

- Example: Parsing and formatting query strings using `querystring.parse()` and `querystring.stringify()`:

```javascript
const querystring = require('querystring');

const queryString = 'name=John&age=30';
const parsedQuery = querystring.parse(queryString);

console.log('Parsed Query:', parsedQuery);
console.log('Formatted Query:', querystring.stringify(parsedQuery));
```

#### 10. `child_process` (Child Processes)

- Example: Spawning a child process to run an external command:

```javascript
const {spawn} = require('child_process');

const child = spawn('ls', ['-l', '-a']);

child.stdout.on('data', (data) => {
    console.log(`Child process output:\n${data}`);
});

child.on('close', (code) => {
    console.log(`Child process exited with code ${code}`);
});
```

These examples demonstrate how to use additional Node.js core modules, such as `events`, `crypto`, `url`, `querystring`,
and `child_process`, to perform various tasks like custom event handling, cryptographic operations, URL parsing, query
string manipulation, and running child processes. Core modules provide a wide range of functionality for different use
cases in Node.js applications.

### Custom Modules

Certainly! Custom modules in Node.js are modules that you create within your project to encapsulate and organize your
code. Here are some examples of how to create and use custom modules:

#### 1. Creating a Local Custom Module

- Example: Create a module named `myModule.js` that exports a function:

```javascript
// myModule.js
function greet(name) {
    return `Hello, ${name}!`;
}

module.exports = {
    greet
};
```

- Example: Import and use the `myModule` module in another file (`app.js`):

```javascript
// app.js
const myModule = require('./myModule');

const greeting = myModule.greet('John');
console.log(greeting); // Output: Hello, John!
```

#### 2. Creating a Custom Module with Multiple Functions

- Example: Create a module named `mathUtils.js` with multiple exported functions:

```javascript
// mathUtils.js
function add(a, b) {
    return a + b;
}

function subtract(a, b) {
    return a - b;
}

module.exports = {
    add,
    subtract
};
```

- Example: Import and use the `mathUtils` module in another file (`app.js`):

```javascript
// app.js
const mathUtils = require('./mathUtils');

const sum = mathUtils.add(5, 3);
console.log('Sum:', sum); // Output: Sum: 8

const difference = mathUtils.subtract(10, 4);
console.log('Difference:', difference); // Output: Difference: 6
```

#### 3. Creating a Custom Module with Classes

- Example: Create a module named `person.js` that exports a class:

```javascript
// person.js
class Person {
    constructor(name, age) {
        this.name = name;
        this.age = age;
    }

    greet() {
        return `Hello, my name is ${this.name} and I'm ${this.age} years old.`;
    }
}

module.exports = Person;
```

- Example: Import and use the `Person` class from the `person` module in another file (`app.js`):

```javascript
// app.js
const Person = require('./person');

const john = new Person('John', 30);
console.log(john.greet()); // Output: Hello, my name is John and I'm 30 years old.
```

#### 4. Creating and Using Custom Modules in Different Folders

- Example: Create a folder named `utils` and place a module named `helper.js` inside it:

```javascript
// utils/helper.js
function formatText(text) {
    return text.toUpperCase();
}

module.exports = {
    formatText
};
```

- Example: Import and use the `formatText` function from the `helper` module in another file (`app.js`):

```javascript
// app.js
const helper = require('./utils/helper');

const formattedText = helper.formatText('Node.js is awesome');
console.log(formattedText); // Output: NODE.JS IS AWESOME
```

These examples illustrate how to create custom modules in Node.js by defining functions and classes within separate
files and then exporting them using `module.exports`. You can organize and encapsulate your code into custom modules to
improve code maintainability and reusability in your Node.js applications.

#### 5. Creating a Custom Module with Private Variables

- Example: Create a module named `counter.js` that exports a function with a private variable:

```javascript
// counter.js
let count = 0;

function increment() {
    count++;
}

function getCount() {
    return count;
}

module.exports = {
    increment,
    getCount
};
```

- Example: Import and use the `counter` module in another file (`app.js`):

```javascript
// app.js
const counter = require('./counter');

counter.increment();
counter.increment();

const currentCount = counter.getCount();
console.log('Current Count:', currentCount); // Output: Current Count: 2
```

#### 6. Creating a Custom Module with Default Export

- Example: Create a module named `defaultModule.js` that exports a single value as the default export:

```javascript
// defaultModule.js
module.exports = 'This is the default export';
```

- Example: Import the default export from the `defaultModule` module in another file (`app.js`):

```javascript
// app.js
const defaultValue = require('./defaultModule');
console.log(defaultValue); // Output: This is the default export
```

#### 7. Creating and Using Custom Modules with ES6 Syntax

- Example: Create a module named `es6Module.js` using ES6 syntax:

```javascript
// es6Module.js
export const message = 'Hello from ES6 module';

export function greet(name) {
    return `Hi, ${name}!`;
}
```

- Example: Import and use the ES6 module in another file (`app.js`) using `import`:

```javascript
// app.js
import {message, greet} from './es6Module';

console.log(message); // Output: Hello from ES6 module

const greeting = greet('Alice');
console.log(greeting); // Output: Hi, Alice!
```

These additional examples demonstrate various scenarios for creating and using custom modules in Node.js, including
modules with private variables, default exports, and modules using ES6 syntax with `import` and `export`. Custom modules
allow you to encapsulate and structure your code effectively, making it easier to manage and reuse in your Node.js
applications.

#### Creating and Using Modules

To create and use modules in Node.js:

1. Create a module by defining variables and functions in a separate `.js` file.
2. Import the module in your main application file using `require()`.
3. Use the functions and variables exported from the module in your application.

Node.js modules are a fundamental part of structuring and organizing code. Core modules provide built-in functionality,
while custom modules allow developers to encapsulate and reuse code. Understanding how to work with modules is essential
for Node.js developers to create modular, maintainable, and scalable applications.

---

## Node.js EventEmitter

Node.js EventEmitter is a built-in module that provides an event-driven programming interface for handling events in
Node.js applications. It allows objects to emit named events and register listeners (functions) to respond to those
events. EventEmitter is a fundamental part of Node.js for building event-driven and asynchronous applications.

### How EventEmitter Works

The EventEmitter module is based on the observer pattern, where an object (the EventEmitter) maintains a list of
listeners (observers) and notifies them when a specific event occurs. Here's how it works:

1. **Create an EventEmitter Object:** You create an instance of the EventEmitter class using `require('events')`.

2. **Define Event Handlers:** You define event handlers (functions) that will be executed when specific events occur.
   These event handlers are also known as listeners.

3. **Emit Events:** You use the `emit()` method to trigger (emit) events with specific names. When an event is emitted,
   all registered listeners for that event are called.

4. **Register Event Listeners:** You use the `on()` or `addListener()` method to register event listeners for specific
   events. These listeners will execute when the corresponding event is emitted.

5. **Execute Event Listeners:** When an event is emitted, all registered event listeners are executed sequentially in
   the order they were registered.

### Example 1: Basic EventEmitter Usage

Let's create a simple example to demonstrate how EventEmitter works:

```javascript
const EventEmitter = require('events');

// Create an instance of EventEmitter
const myEmitter = new EventEmitter();

// Define an event handler (listener)
myEmitter.on('greet', () => {
    console.log('Hello, World!');
});

// Emit the 'greet' event
myEmitter.emit('greet');
```

In this example:

- We create an instance of `EventEmitter` called `myEmitter`.
- We define an event handler (listener) for the 'greet' event using `myEmitter.on('greet', ...)`.

When we emit the 'greet' event using `myEmitter.emit('greet')`, the listener is executed, and 'Hello, World!' is logged
to the console.

### Example 2: Handling Events with Arguments

You can pass arguments to event listeners to handle data associated with an event:

```javascript
const EventEmitter = require('events');

const myEmitter = new EventEmitter();

// Define an event handler with arguments
myEmitter.on('add', (a, b) => {
    const sum = a + b;
    console.log(`Sum: ${sum}`);
});

// Emit the 'add' event with arguments
myEmitter.emit('add', 5, 3);
```

In this example, we define an event handler for the 'add' event that takes two arguments (`a` and `b`) and calculates
their sum.

### Example 3: Registering Multiple Listeners

You can register multiple listeners for the same event, and all of them will be executed when the event is emitted:

```javascript
const EventEmitter = require('events');

const myEmitter = new EventEmitter();

// Define multiple event handlers (listeners)
myEmitter.on('greet', () => {
    console.log('Listener 1: Hello, World!');
});

myEmitter.on('greet', () => {
    console.log('Listener 2: Hi there!');
});

// Emit the 'greet' event
myEmitter.emit('greet');
```

In this example, we register two listeners for the 'greet' event. When the 'greet' event is emitted, both listeners are
executed, resulting in two log messages.

Node.js EventEmitter is a powerful tool for handling events in your applications, allowing you to create event-driven
and asynchronous code. It simplifies communication between different parts of your codebase and is commonly used in
various Node.js libraries and frameworks.

### Example 4: Removing Event Listeners

You can also remove event listeners using the `removeListener()` method. This can be useful when you no longer want a
listener to respond to a specific event:

```javascript
const EventEmitter = require('events');

const myEmitter = new EventEmitter();

// Define an event handler
function greeting() {
    console.log('Hello, World!');
}

// Register the event handler
myEmitter.on('greet', greeting);

// Emit the 'greet' event
myEmitter.emit('greet');

// Remove the event handler
myEmitter.removeListener('greet', greeting);

// Emit the 'greet' event again, but the listener won't execute
myEmitter.emit('greet');
```

In this example, we first register an event handler for the 'greet' event. After emitting the event, we remove the event
handler using `removeListener()`. As a result, when we emit the 'greet' event again, the listener is no longer executed.

### Example 5: Once Listeners

You can use the `once()` method to register listeners that will execute only once for a specific event:

```javascript
const EventEmitter = require('events');

const myEmitter = new EventEmitter();

// Register a once listener
myEmitter.once('greet', () => {
    console.log('Hello, World! (Once)');
});

// Emit the 'greet' event
myEmitter.emit('greet'); // Listener executes

// Emit the 'greet' event again, but the once listener won't execute
myEmitter.emit('greet');
```

In this example, the listener registered with `once()` will execute the first time the 'greet' event is emitted.
Subsequent emissions of the same event will not trigger the listener.

### Example 6: Error Handling with EventEmitter

Emitter objects in Node.js also emit a special 'error' event. To handle errors gracefully, you should always add an
error listener:

```javascript
const EventEmitter = require('events');

const myEmitter = new EventEmitter();

// Error handler
myEmitter.on('error', (error) => {
    console.error('An error occurred:', error.message);
});

// Emit an error
myEmitter.emit('error', new Error('Something went wrong'));
```

In this example, we register an error handler for the 'error' event. When an error is emitted using `emit('error')`, the
error handler is called to handle the error.

These examples demonstrate various aspects of Node.js EventEmitter, including removing listeners, using `once()` for
one-time listeners, and handling errors gracefully. EventEmitter is a versatile tool for event-driven programming in
Node.js, commonly used for building asynchronous and event-based applications.

 
---

## Child Threads

Node.js, known for its single-threaded, event-driven architecture, also offers a mechanism to handle child threads for
parallel processing. In this explanation, we'll delve into how Node.js manages child threads to facilitate concurrent
execution, making it relevant for students, developers, and enthusiasts interested in optimizing performance in Node.js
applications.

### What Are Child Threads?

Child threads, also known as worker threads, are separate threads of execution that can run concurrently with the main (
or parent) thread in a Node.js application. Unlike the main event loop, which is single-threaded, child threads allow
developers to perform CPU-intensive or parallelizable tasks without blocking the main thread's execution.

### Why Use Child Threads?

Node.js's event-driven model excels at handling I/O-bound operations efficiently. However, CPU-bound tasks can
potentially block the main thread, leading to reduced responsiveness and performance. Child threads provide a solution
by offloading such tasks to separate threads, allowing the main thread to continue processing events and responding to
I/O operations.

### `worker_threads` Module

Node.js introduced the `worker_threads` module to enable the creation and management of child threads. This module
offers a built-in and efficient way to leverage multiple threads in Node.js applications.

### Key Components of the `worker_threads` Module

#### 1. Worker Threads:

- Worker threads are instances of the `Worker` class provided by the `worker_threads` module. Each worker thread is a
  separate JavaScript execution context, with its own event loop and memory space.

#### 2. Communication:

- Child threads can communicate with the main thread and other child threads through a message-passing mechanism. They
  can send and receive structured data using the `postMessage()` and `on('message')` methods.

#### 3. Shared Memory:

- While each worker thread has its own memory space, Node.js also provides a `SharedArrayBuffer` that allows data to be
  shared among multiple threads. This shared memory feature can be useful for certain scenarios.

### How Node.js Handles Child Threads

Here's a step-by-step explanation of how Node.js manages child threads:

#### 1. Creating Child Threads:

- Developers create child threads by instantiating instances of the `Worker` class provided by the `worker_threads`
  module.

```javascript
const {Worker, isMainThread, parentPort} = require('worker_threads');

if (isMainThread) {
    // This code runs in the main thread
    const worker = new Worker('./child.js');
    // Handle messages received from the child thread
    worker.on('message', (message) => {
        console.log('Received from child:', message);
    });
    // Send a message to the child thread
    worker.postMessage('Hello from main!');
} else {
    // This code runs in the child thread
    parentPort.on('message', (message) => {
        console.log('Received from main:', message);
        // Send a message back to the main thread
        parentPort.postMessage('Hello from child!');
    });
}
```

#### 2. Communication:

- Child threads communicate with the main thread and other child threads using the `postMessage()` and `on('message')`
  methods.

#### 3. Parallel Execution:

- Child threads run concurrently with the main thread, allowing for parallel execution of tasks. This is especially
  useful for CPU-intensive operations.

#### 4. Event Loop:

- Each child thread has its own event loop, enabling it to handle asynchronous operations independently.

#### 5. Shared Memory (Optional):

- Node.js provides a `SharedArrayBuffer` for sharing data among threads when necessary. Care should be taken to
  synchronize access to shared data to avoid race conditions.

### Use Cases for Child Threads

Child threads in Node.js are valuable for tasks such as:

- CPU-intensive calculations and data processing.
- Parallelizing tasks to improve performance.
- Utilizing multiple CPU cores efficiently.
- Running background tasks without affecting the main thread's responsiveness.

Node.js's ability to handle child threads through the `worker_threads` module extends its capabilities beyond
single-threaded event-driven programming. Child threads provide a means to perform CPU-bound tasks concurrently,
improving the overall performance and responsiveness of Node.js applications. By understanding and utilizing child
threads effectively, developers can optimize their applications to handle a broader range of workloads and deliver
enhanced user experiences.







---







