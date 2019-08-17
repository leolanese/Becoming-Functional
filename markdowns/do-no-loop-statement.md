---
description: 'for, for...of, for...in, while, and do...while.'
---

# Do not loop-statement

## no for use HoF instead

In functional programming we want everthing to be an expression that returns a value. Loops in typescript are statements so they are not a good fit for a functional programming style.

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

Further information: [https://hackernoon.com/rethinking-javascript-death-of-the-for-loop-c431564c84a8](https://hackernoon.com/rethinking-javascript-death-of-the-for-loop-c431564c84a8)

## if inside for-loop (bad idea)

```javascript
const cats = [
  { name: 'Mojo',    months: 84 },
  { name: 'Mao-Mao', months: 34 },
  { name: 'Waffles', months: 4 },
  { name: 'Pickles', months: 6 }
]

var kittens = []  // old for loop 
for (let i = 0; i <= cats.length; i++) { 
  if (cats[i].months === 7) { kittens.push(cats[i].name) } }

console.log(kittens); // ["Waffles", "Pickles"]
```

// better do
```javascript 
const cats = [
  { name: 'Mojo',    months: 84 },
  { name: 'Mao-Mao', months: 34 },
  { name: 'Waffles', months: 4 },
  { name: 'Pickles', months: 6 }
]

const isKitten = cat => cat.months < 7; // check reusability moving parts! 
const getName = cat => cat.name; // sexy code :)

const getKittenNames = cats => cats
      .filter(isKitten)
      .map(getName)
const kittens = getKittenNames(cats);

console.log(kittens); // ["Waffles", "Pickles"]
```

Further Information: [Array.prototype.filter\(\)](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/filter)


### Using .some to break a loop

```javascript
const isBiggerThan10 = numb => numb > 10;
[2, 5, 8, 1, 4].some(isBiggerThan10);  // false
[12, 5, 8, 1, 4].some(isBiggerThan10); // true
```

