Quiver.js
=========

Quiver.js is an experimental JavaScript framework for building web applications using functional programming paradigms. It provides an EDSL to define components with plain functions, which are then composed together and get “compiled” into running application.

## Features

Quiver have many features that are different from traditional web frameworks. In particular:

  - **Composabile Components** - Quiver components are small snippets of plain functions that can easily be reused and composed into larger applications.

  - **Functional Programming** - Quiver makes use of many advanced functional programming concepts borrowed from Haskell. As a result Quiver code base is simpler, cleaner, composable, and more maintainable.

  - **Plain JavaScript** - Despite being type-heavy and functional, Quiver is written in plain JavaScript. This allows easy integration with existing JavaScript libraries and ecosystem. Quiver makes use the latest ES2016+ standard and harness the power of JavaScript, such as prototypal programming and iterators.

  - **CSP Channel** - Quiver data streams are implemented as CSP-like (Communicating Sequential Process) channels. This simplifies the channel implementation and decouple it from raw data sources/sinks. Quiver also introduce the concept of streamable object to allow optimization when transferring data between raw sources and sinks.

  - **Standard Input/Output Streams** - For back end API components, Quiver specifies a Unix-process-like interface with an argument map, input read stream, and returning result stream.

  - **Combinator Pattern** - Quiver makes use of the combinator pattern in Haskell to compose components. As a result Quiver code looks like EDSL (Embedded Domain Specific Language) rather than regular JavaScript.

  - **Functional Reactive Programming (FRP)** - For front end UI components, Quiver provides an FRP-like signal construct and virtual DOM to map between the change in application state and resulting layout.

  - **Type System** - To manage advanced type concepts in JavaScript, Quiver implements a Haskell-like type system in JavaScript. The type system similar to GHC Core language without type inference. It is based on System F and supports type class and parametric polymorphism. Work is being done to also implement dependent type into the system.

## Status

  - Quiver is a solo work by Soares Chen started in 2013 and is still in active development.

  - The back end implementation of Quiver is stable but not battle tested. A major rewrite of the back end is planned once the Quiver type system is fully implemented.

  - The front end implementation is proof of concept. FRP signal works but the dynamic typed nature of JavaScript makes it very error prone to use.

  - Most work is currently being done on implementing a type system in JavaScript. Without that it is hard to make use of more advanced concepts borrowed from Haskell.

## FAQ

  - _Who are you and why should I trust you?_

  I am just a developer who is very passionate in programming language and web development. I think today's web applications are made of big mess of monolithic and imperative code, and functional programming is the way to fix this. It is not easy to fix, but I try hard to make a difference.

  - _Is there any documentation?_

  Some documentation were written few years back. Since then I have acquired more knowledge in functional programming and made many major changes to Quiver. No documentation is planned until the new version of Quiver is done. But I am more than happy to explain in detail if anyone is interested.

  - _Should I try out Quiver myself?_

  Only yes if you are adventurous and are into functional programming. I'll not attempt to convince you on why you should use functional programming. But if you are interested, check out [Eric Elliott's posts](https://medium.com/javascript-scene/the-rise-and-fall-and-rise-of-functional-programming-composable-software-c2d91b424c8c) on functional programming in JavaScript.

  - _Should I use Quiver in production for my company?_

  Almost certainly no, because: 1) It is experimental, 2) Only one person work on it, 3) It is radically different from regular JavaScript.

  You should only consider Quiver if: 1) Your company is large enough to afford experimentation and risk, 2) Your team of front end / back end developers are proficient in functional programming, 3) You are the team leader, trust me enough, and want to hire me to be part of the team.

  - _When will Quiver be ready for use?_

  Not for another few years time. I can only work on Quiver on my personal time because it is too much risk to let a company depend on a framework only one person know, only to leave the company few years later. It also takes time because I am still learning advanced programming language theory topics such as dependent type to be added to Quiver.

  - _Is Quiver better than other web frameworks?_

  Technically, yes. Popularity wise, no. Functional programming is a double edged sword in that it is technically superior but is never likely to gain mainstream adoption. The learning curve is steep and not everyone will find Quiver easy to use.

  - _Why not other functional JavaScript frameworks?_

  Current functional JavaScript frameworks are relatively weak as compared to full fledged functional programming in Haskell. Quiver not only use basic FP concepts like map reduce, but also more advanced concepts such as monad and combinator. Other than that, Quiver aims specifically on web development and provide high level constructs integrated across many domains.

  - _Why is Quiver written in JavaScript? I love functional programming but JavaScript sucks_

  Because _I_ love JavaScript, and I love functional programming too. I think JavaScript is an ugly duckling that deserve more love. Moreover the web ecosystem is overwhelmingly powered by JavaScript. A framework following closely to JavaScript semantics allows easier integration with existing JavaScript ecosystem.

  - _Why not TypeScript / ClojureScript / PureScript / Elm / other transpile-to-JS languages?_

  Same reason as above. Additionally, I like static type system but I want the power of full fledged type systems like Haskell, which not many language provide. But writing Quiver in JS also enables choice. Users of Quiver can choose to write their application either in JS, or any of their favorite language that transpiled to JS.

  - _I am not convinced. JavaScript is the worst language ever._

  I am sorry to hear that. But perhaps do you think so because you still know it as the EcmaScript 3 language specified in 1999? Do check out the ES2016+ standard out there. JavaScript has evolved a long way since then.

  You may see how this is a big challenge for Quiver.js to gain adoption. The target audience tend to be either hard core Haskell/Scala functional programmer or imperative JavaScript programmer. The intersection between these two sets is virtually non-existent.


## Contribution

If you are one of the few persons in this world who likes JavaScript, Haskell, web development, and functional programming, I'd very appreciate if you [drop me a simple message](mailto:soares.chen@gmail.com) saying you like this project.
