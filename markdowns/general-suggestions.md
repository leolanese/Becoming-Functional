# Becoming Functional

> To become Functional we need to start Thinking Functionally. Lets go throw some steps to get **the right mindset into Functional Programming mindset to become into functional**.

Before start: To start with this workshops you need to have an undertanding of what Functional Programming is. You can check this previous workshop: [https://tech.io/playgrounds/0ccbd2817eab67cc4e41211af5c23d1520042/becoming-functional/welcome-](https://tech.io/playgrounds/0ccbd2817eab67cc4e41211af5c23d1520042/becoming-functional/welcome-)

Its main purpose is to abstract control flow and operations on data with functions in order to **avoid "side effects" and "reduce mutation of state" in your code**.

In simple terms, functional programming is a software development style \(a way of writing code\) like OOP, IP, etc. that places a major emphasis on the use of functions.

FP requires you to think a bit differently about how to approach the tasks you’re facing. It’s not a matter of just applying functions to come up with a result; the goal, rather, is to abstract control flows and operations on data with functions in order to avoid side effects and reduce mutation of state in your application.

> FP requires you to think a bit differently about how to approach the tasks you’re facing.

---

## Sugestions about: How to do FP and pure way:

### - In Functional Programming, you don’t just write Pure Functions.

Side effects are good. Functional Languages cannot eliminate Side Effects, they can only confine them. The goal instead is to minimize the amount of impure code

### - In Functinal Programming, you can write your code and then functional decomposition it.

Functional decomposition is athe process of taking a complex process and breaking it down into its smaller, simpler parts.

### - You are already doing FP, but you might not known.

Actually you may be using few features already and you don't know .

### - No assignment.

Changing the value of something already created with = \(var statements with = are fine\)

### - Don't iterate \(for loop, while, etc\), use HoF .map\(\), .reduce\(\), .filter\(\) instead for iterating through an array. \(use recursion instead with tramposling function or high order functions\)

### - Freeze all objects and arrays

Since modifying an existing object or array would be a stateful expression

### - Avoid using Date \(since it always produces a new value no matter what the inputs are\), avoid uisng Math.random \(same reason as Date\) and avoid using mutation methods.

### - A JavaScript Function is a JavaScript Variable until it is executed \(that's to say we can encapsulate it and keep it until evaluated\).

### - Use expressions instead statements \(better don't use if, use shorthand if\)

### - Separate & Minimize moving parts

In a functional program, input flows through a set of functions. Each function operates on its input and produces some output. Functional style discourages functions with side effects that modify internal state or make other changes that aren’t visible in the function’s return value. Functions that have no side effects at all are called purely functional. Avoiding side effects means not using data structures that get updated as a program runs; every function’s output must only depend on its input.

### - Use ES6 Arrow Functions \(fat arrow\) as much as posible

* Arrow functions create a concise expression that "encapsulates" a small piece of functionality. 
* Create a concise expression that encapsulates a small piece of functionality. Additionally, arrows retain the scope of the caller inside the function eliminating the need of self = this.
* Additionally, arrows retain the scope of the caller inside the function eliminating the need of self = this.

```javascript
// old style 
var multiply = function(x,y) { 
  return x * y; } 
  console.log(multiply(2,10)); // 20
}
```

```javascript
// Better do:
// ES6 style
const multiply = (x, y) => x * y;
console.log(multiply(2,10)); // 20
```

Further Information: \[ES6 Arrow functions\]\([https://github.com/leolanese/ES6\_workshop/blob/master/2.2-Arrow functions.md](https://github.com/leolanese/ES6_workshop/blob/master/2.2-Arrow%20functions.md)"\)

### - Bend your language to the problem, not the problem to the language

The most obvios tip is: Please, take advantage of all the language features, if you have something that it is already done, well: use it. Do not spend time working on languague problem, focus on bussiness goal issues

### Function wrapping

```javascript
// fZero() is impure
function fZero() { 
    console.log('IMPURE'); // IO log = Impure
    return 0;
}
```

Controlling the side-effect: A side effect isn’t a side effect until it actually happens. This function wrapping thing is a legitimate strategy. We can keep hiding behind functions as long as we want. Oh yes! And as long as we never actually call any of these functions, they’re all theoretically pure. So, we control the side-effect: Wrapping everything in a function lets us control those effects with precision. We decide exactly when those side effects happen.

```javascript
function returnZeroFunc() {
    function fZero() {  // we wrapped fZero() inside another function that just returned it right?
        console.log('IMPURE');
        return 0;
    }
    return fZero;
}
const zeroFunc1 = returnZeroFunc(); // pure
```

{ 'L e o L a n e s e', 'I B u i l d I n s p i r i n g R e s p o n s i v e S o l u t i o n s',

'L O N D O N , U K' }

My Portfolio [http://www.leolanese.com](http://www.leolanese.com)

My Blog: www.leolanese.com/blog

Twitter: Follow me at:[http://twitter.com/LeoLaneseltd](http://twitter.com/LeoLaneseltd)

Questions / Suggestion / Recommendation ?

