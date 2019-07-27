
# Better ifs

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

### if it is null or empty

// instead of

```javascript
if (y != null && y != '') {}
```

// better do

```javascript
if (y){}
```

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

### nested ifs \(x3 level\)

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

// better do: actions declaration // better do: Method lookup using Command

```javascript
// actions declaration
var greetings = {
  "patrick": sayHello,
  "john": giveSomeNews,
  "jane": sayBye
};

greetings["patrick"](); // sayHello
```

### Ternary operator with return statements

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

### Using operations elements elements

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

#### Function Delegation

Function delegates encapsulate a method allowing functions to be composed or passed as data.

// instead of
```javascript
const a = [0,1,0,3,4,0];
for (i=0; i<a.length; i++){
  if (i[a] === 0){
    console.log(ia[])
  }
}
```


// better do
```javascript
const isZero = n => n === 0;
const a = [0,1,0,3,4,0];
console.log(a.filter(isZero).length); // 3
```


// instead of
```javascript
function fooCall(location) {
  return location;
}
function foo(item, location) {
    if (!item) {
        return false;
    } else if (fooCall(location)) {
        console.log('1')
    } else {
        console.log('0')
    }
}
```

// better do
```javascript
function fooCall(location) {
  return location;
}
function foo(item, location) {
    const fooOne = () => console.log('1');
    const fooTwo = () => console.log('0');
    
    return !!item && (fooCall(location) ? fooOne() : fooTwo());
}
```

#### Function Expressions instead of Function Statements

Statements define an action and are executed for their side effect. Expressions produce a result without
mutating state.

// old style: 'Statement' 
```javascript
const sayHello = function(hour) { 
  var salutation; // temp value 
  if (hour < 12) { 
    salutation = "Good Morning"; 
  } else { 
    salutation = "Good Afternoon" 
  } return salutation; // mutated value 
} 
console.log(sayHello(10)); // Good Morning
```
// Better do: 'Expression'
```javascript
const sayHello = (hour) => hour < 12 ? "Good Morning" : "Good Afternoon";
console.log(sayHello(10)); // Good Morning
```

[https://stackblitz.com/edit/use-expressions-instead-statements?file=index.js](https://stackblitz.com/edit/use-expressions-instead-statements?file=index.js)


### Avoid Nested ifs/complex || conditions

```javascript
// old style var myvar = 1; 
if( myvar==1 || myvar==5 || myvar==7 || myvar==22 ) { true }; // true
```

```javascript
// better but not great :/
const myvar =1;
[1,5,7,22].indexOf(myvar)!== -1; // true
```

// Better do:
```javascript  
const myvar =1; \[1,5,7,22\].includes\(myvar\); // true
```

---

### Better ifs, no ifs: Use functions

// instead of
```javascript
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
  console.log('no color');
  }
}
```

// better do: From Procedural Programming to OOP + FE using an object literal

```javascript
let black = function(){ alert('black') };
let red = function(){ alert('red') };
let blue = function(){ alert('blue') };
let green = function(){ alert('green') };

function getColor(type) {
const colors = {
  'black': black,
  'red': red,
  'blue': blue,
  'green': green,
  'default': function() {
    return 'no color';
  }
  };
  return (colors[type] || colors['default'])();
}
getColor('red'); // alert('red')
```

[https://stackblitz.com/edit/use-functions-no-ifs?file=index.js](https://stackblitz.com/edit/use-functions-no-ifs?file=index.js)

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

This trick works, because the spread operator \(...\) for Array literals does nothing if its operand is an empty Array:

### Conditionally adding properties inside object literals

```javascript
const cond3 = true;
const obj = {
  ...(cond ? {a: 1} : {}),
  b: 2,
};
```

### Breaking or continuing loop: from better-ifs to no-ifs

Using .some() we get iteration functionally similar to .forEach but with the ability to break through return instead. Also there is .every, which can be used. We have to return the opposite boolean compared to .some\(\)

// Using .some() to break a loop

```javascript
const isBiggerThan10 = numb => numb > 10;
[2, 5, 8, 1, 4].some(isBiggerThan10); // false
[12, 5, 8, 1, 4].some(isBiggerThan10); // true
```

// Using .every\(\) to break a loop

```javascript
const isSmallerThan10 = num => num < 10;
console.log([2, 5, 8, 1, 4].every(isSmallerThan10)); // true
console.log([12, 5, 8, 1, 4].every(isSmallerThan10)); // false
```

