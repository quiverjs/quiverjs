Quiver.js
=========

Quiver is a component framework for creating composable and easy to maintain [io.js](https://iojs.org/) applications.

## Architecture

Quiver is made of many layers of [architecture constructs](https://github.com/quiverjs/doc/wiki/Architecture-Constructs) that include:

  - [Stream Channel](https://github.com/quiverjs/doc/wiki/Architecture-Overview#stream-channel) design based on [Communication Sequential Process](http://en.wikipedia.org/wiki/Communicating_sequential_processes) to replace [Node stream](https://iojs.org/api/stream.html)
  - Easy to use [Middleware architecture](https://github.com/quiverjs/doc/wiki/Architecture-Overview#filter), generalized for usage in both HTTP and application logic
  - [Dependency management](https://github.com/quiverjs/doc/wiki/Architecture-Overview#builder) solution to localize all configuration
  - Declarative [Component System](https://github.com/quiverjs/doc/wiki/Component-System) to organize functions into reusable components that can then be combined declaratively.

## io.js and ES6

Quiver runs exclusively on [io.js](https://iojs.org/) and it's source code is written in ES6.

  - Make use of [natively supported](https://iojs.org/en/es6.html) ES6 features by io.js. Including `let` binding, Symbols, and Map.
  - Unsupported ES6 features by io.js are transpiled using
    [Traceur Compiler](https://github.com/google/traceur-compiler)
  - [Promise](http://www.2ality.com/2014/09/es6-promises-foundations.html) based async control flow
  - [Generator support](https://github.com/quiverjs/quiverjs/wiki/Promises#async) on
    top of promises
  - ES6 [Modules](http://www.2ality.com/2014/09/es6-modules-final.html) and Class syntax

## Getting Started

Quiver is made of many small and loosely coupled libraries. The [`quiver-core`](https://github.com/quiverjs/doc/wiki/Core) package provides the core libraries to create custom components in Quiver.

```bash
$ npm install quiver-core
```

A [boilerplate repository](https://github.com/quiverjs/quiver-boilerplate) is provided to help you quickly start developing Quiver applications. Simply [clone the repository](https://github.com/quiverjs/quiver-boilerplate) and start modifying the code base.

## Component

Code in Quiver is organized as many small and reusable components. Here is a
simple hello world handler component:

```javascript
/* hello.js */
import { simpleHandler } from 'quiver-core/component'

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
transpile ES6 code to ES5. In addition use the helper
`startServer()` function in `quiver-core/http` to start up a trivial HTTP server.

```javascript
/* server.js */
import { startServer } from 'quiver-core/http'
import { hello } from './hello.js'

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
$ traceur server.js
```

The [build system](https://github.com/quiverjs/quiverjs/wiki/Build-System) documentation provides more details on running ES6 code on io.js.

## Wiki

Check out the [wiki](https://github.com/quiverjs/doc/wiki) for more detailed
documentation.

## Demo/Tutorial

  - [Demo 01](https://github.com/quiverjs/quiver-demo-01) - This is the first demo to demonstrate how to build simple components in Quiver.js. In this demo, we are going to build a simple HTTP server that greets a user based on the URL path.

## Presentation

  - JSConf.Asia 2014 - [Quiver.js: Rethinking Web Frameworks](https://www.youtube.com/watch?v=Lr-cARL3JXc) ([Slides](http://quiverjs.github.io/jsconfasia-2014))
  - CampJS 2014 - [Quiver.js: A New Server-side Component Architecture](https://www.youtube.com/watch?v=jfaF52FBxEg) ([Slides](http://quiverjs.github.io/slides-01)) (This presentation was based on an older version of Quiver)

## Contribution

Quiver is still in its early stage. You can contribute to Quiver by working on the [issues](https://github.com/issues?q=user%3Aquiverjs+state%3Aopen) and writing your own quiver components.

Right now the [component system](wiki/Component-System) and [core libraries](wiki/Core-Libraries) are almost done and usable right away. However the base architecture is about the same low level as Node. So to build web application in Quiver you still need to write all application code from scratch.

The [core components](wiki/Core-Components) are currently being developed to provide essential web application features such as caching and authentication. With the core components finished, Quiver will be more framework-like with most common features ready out of the box.

## License

[MIT](https://raw.githubusercontent.com/quiverjs/license/master/LICENSE)
