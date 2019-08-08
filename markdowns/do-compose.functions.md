#  Composing functions (to chain)

"At a high level, functional programming is effectively the interplay between decompo-
sition (breaking programs into small pieces) and composition (joining the pieces back together). It’s this duality that makes functional programs modular and so effective." - Functional Programming - Luis Alecio

### Encouraging the decomposition of complex tasks

Thinking functionally typically begins with decomposition by learning to break a particular task into logical subtasks (functions).

// Take the 'string' values from an Array and separate them with ' ':
```javascript
const arr = ['This', 'is', false, null, 'javaScript', 'chau'];
arr.filter(a => typeof a === 'string').join(' '); // 'This is javaScript'
```

---

# Encouraging the composition

> Composition means that we attach multiple functions together, in a pipe.

Composing the functions is actually the easiest part of the whole process. Function composition requires you to write your functions in a composable way. After you have created your functions to be composable, they just kind of stick together.

> Composition is the backbone of modularity in FP

```javascript
const add5 = (b) => 5 + b;
const add3 = (b) => 3 + b;

// no composition
const foo1 = (x) => add5(add3(x));
foo1(2); // 10

// using composition
const foo2 = compose(add5, add3);
foo2(2); // 10
```


### Composing using pipes

Using RxJS we normally chain functions using pipe, Also, pipe return the Observable result of all of the operators having been called in the **order** they were passed in.

> Composition f\(g\(x\)\) and Pipe are both function composition, **what is change is the order: Composition: inside out, Pipe: outside in.***

### Pipe or composition?
- Both can achieve the same results, but pipe are Observables and Observables is the way if we are using rxjs environments.
- Also the difference between compose and pipe is the order of the composition.
- Compose performs a right-to-left function composition since Pipe performs a left-to-right composition.

```javascript
### Use function composition with High Order Functions

```javascript
var cart = [
 {name: "Drink", price: 3.12},
 {name: "Steak", price: 45.15},
 {name: "Drink", price: 11.01}
];

var drinkTotal = cart
 .filter(x => x.name === "Drink") // grab a drink
 .map(x => console.log(x)
 .map(x => x.price) // take only the price from it
 .reduce((t,v) => t +=v) // accumulate all Drink prices
 .toFixed(2); // only takes 2 float numbers
 .map(x => `£${x}`)

console.log(`£${drinkTotal}`);  // $14.13
```




