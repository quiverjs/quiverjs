Quiver.js
=========

Quiver is a middleware-based [Node](http://nodejs.org/) framework for writing modular applications declaratively.

## Features

Quiver provides the following features:

  - [Stream Channel](wiki/Architecture-Overview#stream-channel) design based on [Communication Sequential Process](http://en.wikipedia.org/wiki/Communicating_sequential_processes) to replace [Node stream](http://nodejs.org/api/stream.html)
  - Easy to use [Middleware architecture](Architecture-Overview#filter), generalized for usage in both HTTP and application logic
  - [Dependency management](wiki/Architecture-Overview#builder) solution to localize all configuration
  - Declarative [Component System](wiki/Component-System) to organize functions into reusable components that can then be combined declaratively.

Quiver also make full use of the latest ES6 features:

  - ES6 compiled to ES5 using
    [Traceur Compiler](https://github.com/google/traceur-compiler)
  - [Promise](https://www.promisejs.org/) based async control flow
  - [Generator support](https://github.com/lukehoban/ecmascript-asyncawait) on
    top of promises
  - ES6 Modules and Class syntax

Quiver is NOT an MVC framework. The core Quiver component system is a generic framework to organize web application code. Common application functionalities such as static files and authentication are implemented on top as [Quiver components](wiki/Core-Components).

## Installation

Quiver is made of many small and loosely coupled libraries. To use Quiver, you
need to at least install the `quiver-component` package to define and export
custom components.

```bash
$ npm install quiver-component
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


## Wiki

Check out the [wiki](https://github.com/quiverjs/doc/wiki) for more detailed
documentation.


## Contributors

Author: [Soares Chen](https://github.com/soareschen)

Contributions, feedback, and pull requests welcome!


## License

[MIT](https://raw.githubusercontent.com/quiverjs/license/master/LICENSE)
