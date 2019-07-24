### Avoid impure methods

Pure functions:
1) Given the same input, the function will ALWAYS produce the same output.
2) The function does not rely on any external state whatsoever.
3) A Pure function does not produce any side affects (immutable).

### **Use array manipulation functions & Avoid mutator methods**


**DO NOT** use the mutator methods, these methods modify the array:
.push(), .copyWith(), .fill(), .pop(), .reverse(), .shift(), .sort(), .splice(), .unshift()
Objects, arrays, and functions are mutable.

**Better USE** non-mutating methods (Accessor methods, Iteration methods ):
.concat(), .join(), .slice(), .toString(), .reduce(), .reduceRight(), etc.
JavaScript's primitive data types (Number, String, Boolean, Undefined, and Null) are already immutable.

### Full list:
<a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/prototype#Mutator_methods Mutator_method">Mutator_method</a>


we can use the whole list but mutators methods (These methods do not modify the array and return some representation of the array):
https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/prototype

These methods modify the array:
https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/prototype#Mutator_methods

---
### Do no use random undictable or external methods

// Since it always produces a new value no matter what the inputs are
```javascript
Date (Date.now), Math.random  
```

// reling in external access = side effects
```javascript
console.log(), this, global variables, exceptions thrown, etc.
```
