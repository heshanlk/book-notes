
## 1

### The Node.js Platform

Some principles and design patterns literally define the developer experience with the Node.js platform and its ecosystem. The most peculiar one is probably its asynchronous nature, which makes heavy use of asynchronous constructs such as callbacks and promises

 Approaching Node.js is, in fact, far more than simply learning a new technology: it's also embracing a culture and a community
 
 ### The Node.js philosophy
 
 Every programming platform has its own philosophy, a set of principles and guidelines that are generally accepted by the community, or an ideology for doing things that influence both the evolution of the platform and how applications are developed and designed
 
 #### Small core
 
 The Node.js core—understood as the Node.js runtime and built-in modules
 
 userland (or userspace), which is the ecosystem of modules living outside the core
 
#### Small modules

Node.js uses the concept of a module as the fundamental means for structuring the code of a program. It is the building block for creating applications and reusable libraries.

Not only in code size but also in scope.

Node.js helps to solve the dependency hell problem by making sure that two (or more) packages depending on different versions of the same package will use their own installations of such a package, thus avoiding conflicts. This aspect allows packages to depend on a high number of small, well-focused dependencies without the risk of creating conflicts

 a small module is also:
* Easier to understand and use
* Simpler to test and maintain
* Small in size and perfect for use in the browser

**Don't Repeat Yourself (DRY)**

#### Small surface area

modules is exposing a minimal set of functionalities to the outside world. This has the effect of producing an API that is clearer to use and less susceptible to erroneous usage

In Node.js, a very common pattern for defining modules is to expose only one functionality, such as a function or a class, for the simple fact that it provides a single, unmistakably clear entry point.

Another characteristic of many Node.js modules is the fact that they are created to be used, rather than extended.

#### Simplicity and pragmatism
**Keep It Simple, Stupid (KISS)**

Designing simple, as opposed to perfect

_Pure object-oriented designs often try to replicate the real world using the mathematical terms of a computer system without considering the imperfection and complexity of the real world itself. Instead, the truth is that our software is always an approximation of reality, and we will probably have more success by trying to get something working sooner and with reasonable complexity, instead of trying to create near-perfect software with huge effort and tons of code to maintain._


### How Node.js works

Reactor pattern, which is the heart of the asynchronous nature of Node.js

#### I/O is slow

so the speed and frequency of I/O doesn't only depend on technical aspects, and it can be many orders of magnitude slower than the disk or network. Eg. mouse click is the human intration

#### Blocking I/O

function call corresponding to an I/O request will block the execution of the thread until the operation completes
each I/O operation on a socket will block the processing of any other connection, The traditional approach to solving this problem is to use a separate thread (or process) to handle each concurrent connection.

so having a long-running thread for each connection and not using it for most of the time means wasting precious memory and CPU cycles.

#### Non-blocking I/O

most modern operating systems support another mechanism to access resources, called non-blocking I/O
The most basic pattern for dealing with this type of non-blocking I/O is to actively poll the resource within a loop until some actual data is returned. This is called **busy-waiting**

#### Event demultiplexing

most modern operating systems provide a native mechanism to handle concurrent non-blocking resources in an efficient way. We are talking about the synchronous event demultiplexer (also known as the event notification interface)

multiplexing refers to the method by which multiple signals are combined into one so that they can be easily transmitted over a medium with limited capacity.

Demultiplexing refers to the opposite operation, whereby the signal is split again into its original components.

The synchronous event demultiplexer that we were talking about watches multiple resources and returns a new event (or set of events) when a read or write operation executed over one of those resources completes.

_how the absence of in-process race conditions and multiple threads to synchronize allows us to use much simpler concurrency strategies._

#### The reactor pattern

The main idea behind the reactor pattern is to have a handler associated with each I/O operation. A handler in Node.js is represented by a callback (or cb for short) function.
The handler will be invoked as soon as an event is produced and processed by the event loop.

The asynchronous behavior has now become clear. The application expresses interest in accessing a resource at one point in time (without blocking) and provides a handler, which will then be invoked at another point in time when the operation completes.

_Handles I/O by blocking until new events are available from a set of observed resources, and then reacts by dispatching each event to an associated handler._

#### Libuv, the I/O engine of Node.js

Node.js core team created a native library called libuv, with the objective to make Node.js compatible with all the major operating systems and normalize the non-blocking behavior of the different types of resource

Libuv represents the low-level I/O engine of Node.js and is probably the most important component that Node.js is built on.

libuv also implements the reactor pattern, thus providing an API for creating event loops, managing the event queue, running asynchronous I/O operations, and queuing other types of task.

[An introduction to Libv](http://nikhilm.github.io/uvbook/index.html)

#### The recipe for Node.js

* A set of bindings responsible for wrapping and exposing libuv and other low-level functionalities to JavaScript.
* V8, the JavaScript engine originally developed by Google for the Chrome browser. This is one of the reasons why Node.js is so fast and efficient. V8 is acclaimed for its revolutionary design, its speed, and for its efficient memory management.
* A core JavaScript library that implements the high-level Node.js API.

### JavaScript in Node.js

#### Run the latest JavaScript with confidence

This makes a huge difference as it allows us to target our code for a specific JavaScript and Node.js version, with the absolute guarantee that we won't have any surprises when we run it on production.

#### The module system

CommonJS was a necessary component for Node.js to allow developers to create large and better organized applications on a par with other server-side platforms.

JavaScript has the so-called ES modules syntax (the import keyword may be more familiar) from which Node.js inherits just the syntax, as the underlying implementation is somewhat different from that of the browser.

#### Full access to operating system services

#### Running native code

Node.js is certainly the possibility to create userland modules that can bind to native code.

Node.js officially provides great support for implementing native modules thanks to the N-API interface.

Nowadays, most JavaScript virtual machines (VMs) (and also Node.js) support WebAssembly (Wasm), a low-level instruction format that allows us to compile languages other than JavaScript (such as C++ or Rust) into a format that is "understandable" by JavaScript VMs

### Summary
In this chapter, you have seen how the Node.js platform is built upon a few important principles that shape both its internal architecture and the code we write. You have learned that Node.js has a minimal core, and that embracing the "Node way" means writing modules that are smaller, simpler, and that expose only the minimum functionality necessary.

Next, you discovered the reactor pattern, which is the pulsating heart of Node.js, and dissected the internal architecture of the platform runtime to reveal its three pillars: V8, libuv, and the core JavaScript library.

Finally, we analyzed some of the main characteristics of using JavaScript in Node.js compared to the browser.

Besides the obvious technical advantages enabled by its internal architecture, Node.js is attracting so much interest because of the principles you have just discovered and the community orbiting around it. For many, grasping the essence of this world feels like returning to the origins, to a more humane way of programming in both size and complexity, and that's why developers end up falling in love with Node.js.

In the next chapter, we will go deep into one of the most fundamental and important topics of Node.js, its module system.


