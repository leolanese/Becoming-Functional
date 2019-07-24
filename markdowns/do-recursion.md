# Do recursion

## Recursion

> A recursive function is a function that calls itself until it hits a base case. It is perfectly okay for a function to call itself, as long as it takes care not to overflow the stack. We can use it instead for or while loops

// instead of

```javascript
let i = 0;
for( i; i < 10; i++) {
  console.log( "FP is awesome")
};
```

// better do

```javascript
function counter(value) {
    var i = value;
    if (i < 10) { console.log( "FP counter") } else { return }; // ey! we still use if :(
    counter(++i);
}
```

## Reality check: Tail Call Optimization & Trampoline function

However, while JavaScript’s functional coding style does support recursive functions, we need to be aware that most JavaScript compilers are not currently optimized to support them safely. **We don’t have a standard way to prevent recursive functions from stacking up on themselves indefinitely, and eating away at memory** until they exceed the capacity of the engine. JavaScript recursive functions need to keep track of where they were called from each time, so they can resume at the correct point. There are ways to force JavaScript to perform recursive functions in a safe manner when necessary. For example, it’s possible to construct a custom **trampoline function to manage recursive execution iteratively, keeping only one operation on the stack at a time.**

Easy solution: 1\) Use it recursion carefully with trampoline functions. 2\) Don't iterate \(for loop, while, etc\), but use HoF .map\(\), .reduce\(\), .filter\(\) instead for iterating through an array.

