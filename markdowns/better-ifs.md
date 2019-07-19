## A better ifs? better no if

### **Better ifs or no ifs techniques**

#### Expressions instead of Statements
```javascript runnable
// old style: 'Statement'
const sayHello = function(hour) {
    var salutation; // temp value
    if (hour < 12) {
      salutation = "Good Morning";
    }
    else {
      salutation = "Good Afternoon"
    }
    return salutation; // mutated value
  } 
console.log(sayHello(10)); // Good Morning
```

```javascript runnable
// Better do: 'Expression'
const sayHello = (hour) => hour < 12 ? "Good Morning" : "Good Afternoon";
console.log(sayHello(10)); // Good Morning
```

https://stackblitz.com/edit/use-expressions-instead-statements?file=index.js


### Avoid Nested ifs/complex || conditions

```javascript runnable
// old style
var myvar = 1;
if( myvar==1 || myvar==5 || myvar==7 || myvar==22 ) { true }; // true
```

```javascript runnable
// better but not great :/
const myvar =1;
[1,5,7,22].indexOf(myvar)!== -1; // true
```

```javascript runnable
// Better do:
// a modern approach
const myvar =1;
[1,5,7,22].includes(myvar); // true
```

### Better ifs, no ifs: Use functions

```javascript runnable
// old school 
var color = 'red'

if (color) {
  if (color === 'black') {
    console.log('black');
  } else if (color === 'red') {
    console.log('red');
  } else if (color === 'blue') {
    console.log('blue');
  } else if (color === 'green') {
    console.log('green');
  } else {
    console.log('yellow');
  }
} // red
```

```javascript runnable
// Better do:
const red = function(){ return 'red' };
const blue = function(){ return 'blue' };
const yellow = function(){ return 'yellow' };

function getColor(type) {
  let colors = {
    'red': red,
    'blue': blue,
    'yellow': yellow,
    'default': function() {
      return 'Another color';
    }
  };
  return (colors[type] || colors['default'])();
}
console.log(getColor('red')); // red
```

https://stackblitz.com/edit/use-functions-no-ifs?file=index.js

---

### Conditionally adding elements inside Array literals

```javascript
const arr1 = [];
if (cond) {
    arr1.push('a');
}
arr1.push('b');
```


The following code shows how a boolean cond determines whether or not the element 'a' is added to the Array arr.

```javascript
const cond = true;
const arr2 = [
  ...(cond ? ['a'] : []),
  'b',
];
```
This trick works, because the spread operator (...) for Array literals does nothing if its operand is an empty Array:


### Conditionally adding properties inside object literals


```javascript
const cond3 = true;
const obj = {
  ...(cond ? {a: 1} : {}),
  b: 2,
};
```

### Breaking or continuing loop: from better-ifs to no-ifs
Using .some() we get iteration functionally similar to .forEach but with the ability to break
through return instead. Also there is .every, which can be used. We have to return the opposite
boolean compared to .some()

// Using .some() to break a loop
```javascript
const isBiggerThan10 = numb => numb > 10;
[2, 5, 8, 1, 4].some(isBiggerThan10); // false
[12, 5, 8, 1, 4].some(isBiggerThan10); // true
```

// Using .every() to break a loop
```javascript
const isSmallerThan10 = num => num < 10;
console.log([2, 5, 8, 1, 4].every(isSmallerThan10)); // true
console.log([12, 5, 8, 1, 4].every(isSmallerThan10)); // false
```

---
