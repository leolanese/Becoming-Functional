### function composition: composing functions (to chain)

> Composition means that we attach multiple functions together, in a pipe.

Composing the functions is actually the easiest part of the whole process.
Function composition requires you to write your functions in a composable way.
After you have created your functions to be composable, they just kind of stick together.

> Composition is the backbone of modularity in FP

Using RxJS we normally chain functions using pipe,
Also, pipe return the Observable result of all of the operators having been called in the order they were passed in.

>Composition f(g(x)) and Pipe are both function composition, what is change is the order:
> Composition: inside out, Pipe: outside in.

```javascript
const cart = [
 {name: "Drink", price: 3.12},
 {name: "Steak", price: 45.15},
 {name: "Drink", price: 11.01}
];

const drinkTotal = cart
 .filter(x => x.name === "Drink")
 .map(x => x.price)
 .reduce((t,v) => t +=v)
 .toFixed(2);

console.log(`£${drinkTotal}`);  // $14.13
```

