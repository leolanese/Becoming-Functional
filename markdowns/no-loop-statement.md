### no-loop-statement: for, for...of, for...in, while, and do...while.

In functional programming we want everthing to be an expression that returns a value. 
Loops in typescript are statements so they are not a good fit for a functional programming style. 

// instead of
```javascript
const numbers = [1, 2, 3];
const double = [];
for (let i = 0; i < numbers.length; i++) {
  double[i] = numbers[i] * 2;
}
```

// better do
```javascript
const numbers = [1, 2, 3];
const double = numbers.map(n => n * 2);
```

Further information:
https://hackernoon.com/rethinking-javascript-death-of-the-for-loop-c431564c84a8


