
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

**
Don't Repeat Yourself (DRY)**

#### Small surface area

modules is exposing a minimal set of functionalities to the outside world. This has the effect of producing an API that is clearer to use and less susceptible to erroneous usage

In Node.js, a very common pattern for defining modules is to expose only one functionality, such as a function or a class, for the simple fact that it provides a single, unmistakably clear entry point.

Another characteristic of many Node.js modules is the fact that they are created to be used, rather than extended.

#### Simplicity and pragmatism
**
Keep It Simple, Stupid (KISS)**

Designing simple, as opposed to perfect
_
Pure object-oriented designs often try to replicate the real world using the mathematical terms of a computer system without considering the imperfection and complexity of the real world itself. Instead, the truth is that our software is always an approximation of reality, and we will probably have more success by trying to get something working sooner and with reasonable complexity, instead of trying to create near-perfect software with huge effort and tons of code to maintain._


### How Node.js works

Reactor pattern, which is the heart of the asynchronous nature of Node.js

#### I/O is slow

so the speed and frequency of I/O doesn't only depend on technical aspects, and it can be many orders of magnitude slower than the disk or network. Eg. mouse click is the human intration


 
