Quiver.js
=========

Quiver is a middleware-based [Node](http://nodejs.org/) framework for writing modular applications declaratively.

## Features

Quiver provides the following features:

  - [Stream Channel](https://github.com/quiverjs/doc/wiki/Architecture-Overview#stream-channel) design based on [Communication Sequential Process](http://en.wikipedia.org/wiki/Communicating_sequential_processes) to replace [Node stream](http://nodejs.org/api/stream.html)
  - Easy to use [Middleware architecture](https://github.com/quiverjs/doc/wiki/Architecture-Overview#filter), generalized for usage in both HTTP and application logic
  - [Dependency management](https://github.com/quiverjs/doc/wiki/Architecture-Overview#builder) solution to localize all configuration
  - Declarative [Component System](https://github.com/quiverjs/doc/wiki/Component-System) to organize functions into reusable components that can then be combined declaratively.

Quiver also make full use of the latest ES6 features:

  - ES6 compiled to ES5 using
    [Traceur Compiler](https://github.com/google/traceur-compiler)
  - [Promise](https://www.promisejs.org/) based async control flow
  - [Generator support](https://github.com/lukehoban/ecmascript-asyncawait) on
    top of promises
  - ES6 Modules and Class syntax

Quiver is NOT an MVC framework. The core Quiver component system is a generic framework to organize web application code. Common application functionalities such as static files and authentication are implemented on top as [Quiver components](https://github.com/quiverjs/doc/wiki/Core-Components).

## Wiki

Check out the [wiki](https://github.com/quiverjs/doc/wiki) for more detailed
documentation.

## Demo/Tutorial

  - [Demo 01](https://github.com/quiverjs/quiver-demo-01) - This is the first demo to demonstrate how to build simple components in Quiver.js. In this demo, we are going to build a simple HTTP server that greets a user based on the URL path.

## Presentation

  - JSConf.Asia 2014 - [Quiver.js: Rethinking Web Frameworks](https://www.youtube.com/watch?v=Lr-cARL3JXc) ([Slides](http://quiverjs.github.io/jsconfasia-2014))

## Installation

Quiver is made of many small and loosely coupled libraries. The [`quiver-core`](https://github.com/quiverjs/doc/wiki/Core) package provides the core libraries to create custom components in Quiver.

```bash
$ npm install quiver-core
```

## Component

Code in Quiver is organized as many small and reusable components. Here is a
simple hello world handler component:

```javascript
/* hello.js */
import { simpleHandler } from 'quiver-component'

export var hello = simpleHandler(
  args => 'Hello World',
  'void', 'text')
```

Here `simpleHandler` is a simplified component type.

  - `args` is a plain object for storing parameterized input. (i.e. query
    string)
  - Input type `void` means the handler ignores the input stream. (i.e. request
    body)
  - Output type `text` means the handler returns a string. We use the word
    "text" to avoid overriding reserved methods like `.toString()`.

`simpleHandler` is not a HTTP handler. But it can be used for handling HTTP
requests or used in many other ways.

## Running Server

[Traceur Compiler](https://github.com/google/traceur-compiler) is required to
transpile ES6 code to ES5. In addition install `quiver-http` to use the helper
`startServer()` function to start up a trivial HTTP server.

```javascript
/* server.js */
import { startServer } from 'quiver-http'
import { hello } form './hello.js'

// placeholder empty config
var config = { }

startServer(hello, config)
.then(server => {
  console.log('Demo server running at port 8080...')
})
.catch(err => {
  console.log('error starting server:', err)
})
```

```bash
$ npm install -g traceur
$ npm install quiver-http
$ traceur server.js
```

## Quiver in ES5

All official Quiver libraries are transpiled and exported as ES5 code. You may
write Quiver applications in ES5, but it is much more beneficial to code in ES6.
You will find out how much cleaner it is to code in Quiver because of ES6!

## Status

Quiver is currently still in beta development. Right now the [component system](wiki/Component-System) and [core libraries](wiki/Core-Libraries) are almost done and usable right away. However the base architecture is about the same low level as Node. So to build web application in Quiver you still need to write all application code from scratch.

The [core components](wiki/Core-Components) are currently being developed to provide essential web application features such as caching and authentication. With the core components finished, Quiver will be more framework-like with most common features ready out of the box.

It is your chance to contribute right now by writing common quiver components to build up the Quiver ecosystem.

## Community

Quiver is just starting to build its community. Be the first to join the Quiver community!

  - [Google Groups](https://groups.google.com/d/forum/quiverjs)

## Contributors

Author: [Soares Chen](https://github.com/soareschen)

Contributions, feedback, and pull requests welcome. Please [contact me](mailto:soares.chen@gmail.com) if you have tried Quiver in any way or is interested on helping the project.


## License

[MIT](https://raw.githubusercontent.com/quiverjs/license/master/LICENSE)
