## FP definitions: features and concepts

1- First-Class citizens: <br />
mean that you can STORE functions into a variable
<br />
2- High-Order function: HoF <br />
A higher-order function is a function that can take another function as an argument, 
or that returns a function as a result. f() are not just methods. they can return f() or receive other f() as params (callbacks)
<br />
3- Pure functions: <br />
Given the same inputs, always returns the same output, and no side-effects 
<br />
4- Immutability State: <br />
Immutable objects never change
<br />
5- Recursion: <br />
Is a f() simply calls itself.
<br />
6- Currying: <br />
Since Javascript has higher-order functions we can call functions with some of its arguments pre-filled
<br />
7- Memoisation: <br />
Functions that are expensive to run can be performance optimised with memoisation. 
This involves using a closure to cache the results of previous calls to the function
<br />
8- Function composition: <br />
Is the process of combining two or more functions in order to produce a new function or perform some computation.
<br />
9- Reactive Functional Programming: <br />
Reactive Programming is a paradigm where "async data streams" can be used almost everywhere. Everything is a stream.
<br />
10- Side effects: <br />
We need to write functions/methods that limiting the side effects
<br />
11- Declarative paradigm: <br />
FP is a declarative paradigm software development style, like IP or OOP, thats keeps 'functions' and 'data' separate
<br />
12- Composing functions: Compose & Pipe <br />
Composition means that we attach multiple functions together, in a pipe, where the return value
of the first function becomes the input for the next function.
<br />
13- Shared State": <br />
FP avoids shared state, instead relying on immutable data structures and pure calculations.
Shared state is any variable, object, or memory space that exists in a shared scope, or as the property of an object being passed between scopes. 
<br />
14- Pure Function" (used on reducer) <br />
A pure function is a function which:
  - Given the same input, always return the same output (pure)
  - Has no side effects (immutable)
<br />
15- Side-effects  <br />
Mutating data can cause unintended side-effects.
<br />
16: Js First-Class: <br /> 
Functions in JS are "first-class" objects, this means that something has a value
<br />
17: First-Class-functions: FcF <br />
Functions in JavaScript are treated as objects, not just methods: mean that you can STORE functions into a variable
<br />
18- Referential transparency: <br />
It is the fact that an expression, in a program, may be replaced by its value (or anything having the same value) without 
changing the result of the program. This implies that methods should always return the same value for a given argument, 
without having any other effect. This functional programming concept also applies to imperative programming, though,
and can help you make your code clearer.
<br />
19- Functor: <br />
A functor is something that can be mapped over. In other words, it’s a container which has an interface which can be used to apply a function to the values inside it. When you see the word functor, you should think "mappable".
<br />
