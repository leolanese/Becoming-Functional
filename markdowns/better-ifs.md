## A better ifs? better no if

### **Better ifs or no ifs techniques**

## Keep i'f' simple

// instead of
```javascript
if (condition) {
  dosomething();
}
```

// better do
```javascript
condition && dosomething();
```

---

### if it is null or empty

// instead of
```javascript
if (y != null && y != '') {}
```
// better do
```javascript
if (y){}
```


---

### keep i'f' and else simple

// instead of
```javascript
if (a === b) {
  return true;
} else {
  return false;
}
```

// better do
```javascript
return a === b;
```


---
### nested ifs (x3 level)

// instead of
```javascript
// pattern
function sayHello () {
  console.log( "sayHello" );
}
function giveSomeNews () {
  console.log( "giveSomeNews" );
}
function sayBye () {
  console.log( "sayBye" );
}

// declaring name for testing
let name = "patrick";
// var name = "jane";

if( name === "patrick" ) {
    sayHello();
  } else if( name === "jane" ) {
    giveSomeNews();
  } else {
    sayBye();
}

// sayHello
```

// better do: actions declaration
// better do: Method lookup using Command
```javascript
// actions declaration
var greetings = {
  "patrick": sayHello,
  "john": giveSomeNews,
  "jane": sayBye
};

greetings["patrick"](); // sayHello
```




---

### Ternary operator with return statements

```javascript
if ( 'undefined' !== typeof nn['key'] ) {
  var gradeObject.title;
}
if (gradeObject.value === gradeValue) {
  return gradeObject.title;
}
```

// better do
```javascript
return gradeObject.title ?
'undefined' !== typeof nn['key'] : gradeObject.value === gradeValue;
```
---

### Ternary operator with return statements: return boolean ? ‘foo’ : ‘bar’;

// instead of
```javascript
if ( 'undefined' !== typeof nn['key'] ) {
  var gradeObject.title;
}
if (gradeObject.value === gradeValue) {
 return gradeObject.title;
}
```

// better do
```javascript
return gradeObject.title ?
        'undefined' !== typeof nn['key'] : gradeObject.value === gradeValue;
```        
---

###  Using operations elements elements

// instead of
```javascript
const values = [1, 2, 3];
let sum = 0;
for (const x of values) {
  sum = sum + x;
}
```

// better do
```javascript
const values = [1, 2, 3];
const add = (x, y) => x + y;
const sum = values.reduce(add);
```

---

### Setting properties 

// instead of
```javascript
const obj = {
	one: 1
}
obj.two = 2
```

// better do
```javascript
const obj = {
	one: 1
}
const newObj = {
	...obj,
	two: 2
}
```

---

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
