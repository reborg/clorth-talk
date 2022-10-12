## Wed 12 Oct 2022 09:09:55 BST

These are thoughts regarding what could go on the slides, general flow of ideas etc.

* [x] Why implementing a Clojure compiler for Forth?
  * Mostly fun really, take my brain away from daily programming routine into a familiar, isolated territory
  * Forces you to read the X-language manual and understand it
  * Go along implementing it and make larger and larger programs on the side
  * Enjoying the process so much I'm probably going to do similar project around other great languages.
* Why Forth?
  * Just heard about Forth many times and picked it to understand more
  * Last time being the inspiration for Michelson, the language for smart contracts in Tezos
  * Forth has been mentioned for reflection capabilities (just change the dictionary)
  * Forth has a minimal approach that mimics the CPU (and an assembler mode that would be nice to explore)
* [x] A quick introduction to Forth,
  * This is necessary to understand how one would go about implementing a parser for it
  * Forth is a concatenative, procedural, stack based language
  * Concatenative: there are no lambdas, or functional construction with parameters, there is the implicit stack for that
  * Concatenative: program composition happens by concatenation of words, instead of composition of functions.
  * There is also no "calling a function", the parser understands either words or elementary types.
  * DEMO: put things on the stack, drop them, swap etc.
  * Is it pure? Not normally, stack is mutable, variables are global, normally everything is based on memory locations
* [x] Options for language development in Clojure
  * Start from the grammar, generate an Instaparse parser. Good for complicated grammars.
  * Use the Clojure reader: good for Lispy internal DSLs
  * Roll your own: only if simple case
* The fundamental pieces
  * The REPL interaction experience
  * The Reader
  * The "compiler"
*  Could showcase a small quickly create your language interpreter top-down: an infix calculator!
  *  Could then show how that stretches into Clorth
* Some features
  * Immutable stack: concurrency ready
  * Two level of native calls!
* What's Next for Clorth
  * Variables
  * Arrays
  * meta-programming (Execute)

## TODO

* [ ] Replace links to local images with the github raw equivalent [1]

### Useful snippets

* [1] <img src="https://raw.githubusercontent.com/reborg/clorth-talk/master/202210-clojurians-meetup/media/pic.png" width="600">
* <small>Small but not too much</small>
* Table:

      |Part |Name       |Bits  |Fn |
      |-----|-----------|------|---|
      |w    |whole-word |0-35  |cwr|
      |p    |prefix     |0-1-2 |cpr|

      **C** (content of the) <name> **R** (egistry)

* Quote:

> This is a deep quote
