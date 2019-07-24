# Becoming Functional

> To become Functional we need to start Thinking Functionally. Lets go throw some steps to get **the right mindset into Functional Programming mindset to become into functional**.

Before start:
To start with this workshops you need to have an undertanding of what Functional Programming is.
You can check this previous workshop: https://tech.io/playgrounds/0ccbd2817eab67cc4e41211af5c23d1520042/becoming-functional/welcome-

Its main purpose is to abstract control flow and operations on data with functions in order to **avoid
"side effects" and "reduce mutation of state" in your code**.

In simple terms, functional programming is a software development style (a way of writing code) like OOP, IP, etc.
that places a major emphasis on the use of functions. 

FP requires you to think a bit differently about how to approach the tasks you’re facing. It’s not a matter of just applying functions to come up with a result; the goal, rather, is to abstract control flows and operations on data with functions in order to avoid side effects and reduce mutation of state in your application.

> FP requires you to think a bit differently about how to approach the tasks you’re facing.

***
## Sugestions about: How to do FP and pure way:

### - In Functional Programming, you don’t just write Pure Functions.
Side effects are good. Functional Languages cannot eliminate Side Effects, they can only confine them. 
The goal instead is to minimize the amount of impure code

### - In Functinal Programming, you can write your code and then functional decomposition it.
Functional decomposition is athe process of taking a complex process and breaking it down into its smaller, simpler parts.

### - You are already doing FP, but you might not known.
Actually you may be using few features already and you don't know .

### - No assignment. 
Changing the value of something already created with = (var statements with = are fine)

### - Don't iterate (for loop, while, etc), use HoF .map(), .reduce(), .filter() instead for iterating through an array. (use recursion instead with tramposling function or high order functions)

### - Freeze all objects and arrays
Since modifying an existing object or array would be a stateful expression

### - Avoid using Date (since it always produces a new value no matter what the inputs are), avoid uisng Math.random (same reason as Date) and avoid using mutation methods.

### - A JavaScript Function is a JavaScript Variable until it is executed (that's to say we can encapsulate it and keep it until evaluated).

### - Use expressions instead statements (better don't use if, use shorthand if)

### - Separate moving parts

In a functional program, input flows through a set of functions. Each function operates on its input and produces some output.
Functional style discourages functions with side effects that modify internal state or make other changes that aren’t
visible in the function’s return value. Functions that have no side effects at all are called purely functional.
Avoiding side effects means not using data structures that get updated as a program runs; every function’s
output must only depend on its input.






