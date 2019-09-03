## FP definitions: features and concepts

1- First-Class citizens: 
mean that you can STORE functions into a variable
2- High-Order function: HoF 
A higher-order function is a function that can take another function as an argument, 
or that returns a function as a result. f() are not just methods. they can return f() or receive other f() as params (callbacks)
3- Pure functions: Given the same inputs, always returns the same output, and no side-effects 
4- Immutability State: 
Immutable objects never change
5- Recursion: 
Is a f() simply calls itself.
6- Currying: 
Since Javascript has higher-order functions we can call functions with some of its arguments pre-filled
7- Memoisation: 
Functions that are expensive to run can be performance optimised with memoisation. 
This involves using a closure to cache the results of previous calls to the function
8- Function composition: 
Is the process of combining two or more functions in order to produce a new function or perform some computation.
9- Reactive Functional Programming: 
Reactive Programming is a paradigm where "async data streams" can be used almost everywhere. Everything is a stream.
10-Side effects:
We need to write functions/methods that limiting the side effects
11: Declarative paradigm:
FP is a declarative paradigm software development style, like IP or OOP, thats keeps 'functions' and 'data' separate
12: "composing functions": Compose & Pipe
Composition means that we attach multiple functions together, in a pipe, where the return value
of the first function becomes the input for the next function.
13: "shared state": 
FP avoids shared state, instead relying on immutable data structures and pure calculations.
Shared state is any variable, object, or memory space that exists in a shared scope, or as the property of an object being passed between scopes. 
14: "pure function" (used on reducer)
A pure function is a function which:
  - Given the same input, always return the same output (pure)
  - Has no side effects (immutable)
15: "side-effects" 
Mutating data can cause unintended side-effects.
16: "Js First-Class" 
Functions in JS are "first-class" objects, this means that something has a value
17: "First-Class-functions" FcF
Functions in JavaScript are treated as objects, not just methods: mean that you can STORE functions into a variable
18: "Referential transparency"
It is the fact that an expression, in a program, may be replaced by its value (or anything having the same value) without 
changing the result of the program. This implies that methods should always return the same value for a given argument, 
without having any other effect. This functional programming concept also applies to imperative programming, though,
and can help you make your code clearer.
