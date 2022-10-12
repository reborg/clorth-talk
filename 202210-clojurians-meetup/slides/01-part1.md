#### <small></small>

<img src="https://raw.githubusercontent.com/reborg/clorth-talk/master/202210-clojurians-meetup/media/reclojure.png" width="600">

* reclojure.org 2022 is just around the corner!
* The CfP is still open! Hurry up!
* https://sessionize.com/reclojure-2022/

# Many flavours of "why"?

* Why implementing a language?
* Why implementing a language in Clojure?
* Why implementing Forth in Clojure?

# Why implementing a language?

* Effective way to learn
* Getting familiar with different way of thinking programs
* Trick famously popularized "The Pragmatic Programmer" book:

>
<small>
Learn at least one new language every year. Different languages solve the same problems in different ways. By learning several different approaches, you can help broaden your thinking and avoid getting struck in a rut.
</small>

# <small>Why implementing a language in Clojure?</small>

Well, it's the language I'm most fluent with...

## but also
## Clojure has a customisable REPL
## Great for both internal (lispy) or external DSLs
## Clojure has great multimethod dispatch facilities

# Why Forth?

* What if Clojure didn't have parenthesis?
* Simple language with almost no grammar
* Yet expressive and powerful
* Heard about it: Michelson, Nasa, etc.
* Great for writing DSLs

# Forth programs are actually DSLs!

Here's a small program.

What do you think this is going to print?

```forth
line dot line dot dot cr
```

<small>Let me show you...</small>

# Functional vs Concatenative

* Clojure is **applicative:** it executes by applying `f` to `args`
* A program is written by **composing** functions

* Forth is **concatenative:** it executes by invoking words
* A program is written by **concatenating** words
* The stack is implicit, no `args` required

# Let me show you…
