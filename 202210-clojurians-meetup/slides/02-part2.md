# Recipe: implementing a language

You might need some or all of the following:

* A **Reader** (string -> data structure)
* A **Parser** (data structure -> other representation)
* An **Interpreter** (data structure -> evaluation)
* A **Compiler** (data structure -> executable)

# The Reader

* If the language is Lispy use the Clojure reader
  * Plenty of examples: `core.test`, `core.async`
* If not Lispy you can:
  * Instaparse it
  * Hybrid approach (Clorth)
  * Roll your own

# The Forth Grammar

##
## Are you ready?
## <small>`non_empty_word_list = word { space word }`</small>

# The Clorth Reader

```clojure
(def reader-specials
  {":" "\\:" ";" "\\;" "~" "\\~"}) ;; A few more

(defn handle-specials [s]
  (reduce (fn [s [s1 s2]]
            (string/replace s s1 s2))
    s reader-specials))

(defn read [s]
  (read-string (str "[" (handle-specials s) "]")))

;; Approach: move the tokens into a vector, parse the tokens
;; Challenge: some Forth tokens are not valid Clojure symbols.
```

# The Parser

* The parser transforms the initial reading
* Normally it enriches tokens with semantic information
* The information is used for evaluation or compilation
* This is not an universal rule!
* Clorth doesn't really have a parser.

# The Interpeter

* Interpretation evaluates the language at the interpreter level itself
* Compilation is a level down (e.g. JVM, machine language etc.)
* The lower the level the faster the speed
* Clorth has currently a simple token interpreter

# Tangent: Interpreter VS compilation levels

* `1+` invokes `inc` that increments a number on the stack (Program level 0)
* `1+` becomes a function that increments a number on the stack (Program level -1)
* `1+` becomes bytecode `iadd` that increments an item from the JVM stack (Program level -2)
* `1+` becomes `inc` i386 instruction that increments a CPU register (Program level -4)

# The Clorth Interpreter

```clojure
(defmulti word
  (fn [_ args] (cond-> args (coll? args) first)))

(defmethod word 'drop
  [env args]
  (word (pop1 env) (rest args)))
```

# The Clorth REPL

* Clojure comes with `clojure.main/repl`
* This is a small API to create your own REPL
* As expected it gives you a `:read` and an `:eval` options
* The Print/Loop part is taken care of
* Let me show you...

# Some hidded features

* The stack is immutable and passed as a parameter while interpreting
* There is interop to call into Clojure functions
* To go native, use the "\_" prefix in front of a word
* Error messages are as simple as possible, no Java Exceptions
* Multimethods are split by namespaces: stdblib, math and soon others.
