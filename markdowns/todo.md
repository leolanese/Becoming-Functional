# todo


## **Use Function Delegation**

Why: Function delegates encapsulate a method allowing functions to be composed or passed as data.

```javascript 
const addOne = n =&gt; n + 1; const isZero = n =&gt; n === 0; const addValues = \(x,y\) =&gt; x + y; const giveMeTheKey = x =&gt; x.age === 38;

console.log\(addOne\(1\)\); // 2 console.log\(isZero\(addValues\(-5, 5\)\)\); // True  
console.log\(\[0,1,0,3,4,0\].filter\(isZero\).length\); // 3

let yoGiveMeTheKey = \[{ "name": "Zak", "age": 25 },{ "name": "Adel", "age": 38 },{ "name": "Yori", "age": 28 }\].filter\(giveMeTheKey\); console.log\(JSON.stringify\(yoGiveMeTheKey\)\);

```text
https://stackblitz.com/edit/function-delegation


***
### **Separate the pure from the impure**
If a function is impure, if posible, split it and simple as creating two functions

***

### All useful Pure Functions must return something

```javascript
function addNoReturn(x, y) {
    var z = x + y
}
```

Notice how this function doesn’t return anything. It adds x and y and puts it into a variable z but doesn’t return it. It’s a pure function since it only deals with its inputs. It does add, but since it doesn’t return the results, it’s useless.

## **Don't change objects in functions**

\`\`\`javascript runnable // IMPURE MUTATED :\( const minimum = { usa: { old: 16 }, spain: 21, uk: 19 }

function save\(object\){ object.saved = true; // don’t return object; }

```text
```javascript runnable
// Better do:
// PURE
const minimum = {
  usa: { old: 16 },
  spain: 21,
  uk: 19
}

// Write functions that return altered copies instead of changing properties of the given object.
function save(object){
    let newObject = {...object, newProp: true}; // clone it first :)
    return newObject;
}
// new object changed
JSON.stringify(save(minimum)) // "{"usa":{"old":16},"spain":21,"uk":19,"newProp":true}"

// original object NOT changed
JSON.stringify(minimum); // "{"usa":{"old":16},"spain":21,"uk":19}"
```

## **Avoid loops and iterations**

Ej1\)

A loop is an imperative control structure that is hard to reuse and difficult to plug in to other operations. We can use: Recursion,.map\(\), .reduce\(\), .filter\(\), etc

Why:

* make the code clean
* make the logic reusable
* minimizing moving parts
* make it more reusable and portable

\`\`\`javascript runnable // Old style // take an array of Object just get an specific key\(s\) // Using old imperative programming var ao = \[{ "name": "Zak", "age": 25 },{ "name": "Adel", "age": 38 },{ "name": "Yori", "age": 28 } \]; for \(var i = 0, arr = \[\]; i &lt; ao.length; i++\) { arr.push\(ao\[i\].name\); // mutation sucks :\( };  
console.log\(arr\); // \["Zak", "Adel", "Yori"\]

```text
```javascript runnable
// better: using FP, avoid loops
const x = (x) => x.name; // minimizing moving parts
[{
        "name": "Zak",
        "age": 25
    },{
        "name": "Adel",
        "age": 38
    },{
        "name": "Yori",
        "age": 28
    }
].map(x); // ["Zak", "Adel", "Yori"]
```

Ej2) 
```javascript
// Using .some to break a loop 
const isBiggerThan10 = numb =&gt; 
numb &gt; 10; \[2, 5, 8, 1, 4\].some\(isBiggerThan10\); // false \[12, 5, 8, 1, 4\].some\(isBiggerThan10\); // true

```text
```javascript runnable
// Using .every to break a loop
const isSmallerThan10 = num => num < 10;
console.log([2, 5, 8, 1, 4].every(isSmallerThan10));  // true
console.log([12, 5, 8, 1, 4].every(isSmallerThan10)); // false
```

Tip: Think about results over steps. Next time you are about to iterate something, stop, and think about: "How this can look if I don't iterate this?" [Loops & Iteration](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Loops_and_iteration)

## loops and other imperatives things

\`\`\`javascript runnable // simple loop construct var acc = 0; for \(var i = 1; i &lt;= 10; ++i\) acc += i; console.log\(acc\); // prints 55 // without loop construct or variables \(recursion\) function sumRange\(start, end, acc\) { if \(start &gt; end\) return acc; return sumRange\(start + 1, end, acc + start\) } console.log\(sumRange\(1, 10, 0\)\); // prints 55

```text
Tip: Notice how recursion, the functional approach, accomplishes the same as the for loop by calling itself with a new start (start + 1) and a new accumulator (acc + start). It doesn’t modify the old values. Instead it uses new values calculated from the old.


***



***

### **Use Higher-order-Function (HoF) & Spread Operator when possible**

```javascript runnable
let jsonData = [
  { id: 1, name: "Soda", price: 2.40, cost: 1.04, size: "4cl", },
  { id: 2, name: "Beer", price: 6.00, cost: 2.45, size: "8cl" },
  { id: 3, name: "Margarita", price: 10, cost: 4.45, size: "12cl" }
];

// ...x (spread operator) ensures that we copy the complete object and its properties, while only modifying the price value. 
const objAndProperties = jsonData
                        .map(x => ({...x, price: (x.price / 2).toFixed(1) }));

console.log(JSON.stringify(objAndProperties)); // [{"id":1,"name":"Soda","price":"1.2","cost":1.04,"size":"4cl"},{"id":2,"name":"Beer","price":"3.0","cost":2.45,"size":"8cl"},{"id":3,"name":"Margarita","price":"5.0","cost":4.45,"size":"12cl"}]
```

\`\`\`javascript runnable // var arrOfObj = \[ { "name": "Sam", "age": 1 }, { "name": "Tom", "age": 2}, { "name": "Carley","age": 35} \];

// this is so 2014 - ES4.1 var arrToFilter = \[\]; for \(var i=0; i &lt; arrOfObj.length; i++\){ arrToFilter.push\(arrOfObj\[i\].name\); } console.log\(arrOfObj\)

// better ES6 style & using .map\(\) let arrToFilter = arrOfObj.map\(arr =&gt; arr.name\);

```text
***

### **Use Method Chaining**
Method chains allow a series of functions to operate in succession to reach a final result. Method chains allow 
function composition similar to a pipeline.

```javascript runnable
let cart = [{name: "Drink", price: 3.12}, 
            {name: "Steak", price: 45.15}, 
            { name: "Drink", price: 11.01}];
let drinkTotal = cart.filter(x=> x.name === "Drink")
                     .map(x=> x.price)
                     .reduce((t,v) => t +=v)
                     .toFixed(2); 
console.log('Total Drink Cost', drinkTotal ); // Total Drink Cost $14.13
```

## **Use pipelines**

A pipeline allows for easy function composition when performing multiple operations on a variable. Since JavaScript lacks a Pipeline operator, a design pattern can be used to accomplish the task.

\`\`\`javascript runnable const pipe = functions =&gt; data =&gt; { return functions.reduce\( \(value, func\) =&gt; func\(value\), data \); };

let cart = \[3.12, 45.15, 11.01\]; const addSalesTax = \(total, taxRate\) =&gt; \(total \* taxRate\) + total;

const tally = orders =&gt; pipe\(\[ x =&gt; x.reduce\(\(total, val\) =&gt; total + val\), // sum the order x =&gt; addSalesTax\(x, 0.09\), x =&gt; `Order Total = ${x.toFixed(2)}` // convert to text \]\)\(orders\); // Order Total = 64.62

```text
***


### **Dependency injection**
Dependency injection works by moving the impure parts of the code out of the function. 
So you have to pass them in as parameters. 

```javascript runnable
// Here we are using: 
// new Date()).toISOString() = IMPURE
// console.log(); = IMPURE

const d = {toISOString: () => '1865-11-26T16:00:00.000Z'};
// IMPURE 
function logSomething(foo) {
    const dt = (new Date()).toISOString(); // Date is impure
    console.log(`${dt}: ${foo}`); // IO log is impure
    return foo;
}

logSomething('Date is impure! & IO log is impure :(');
```

`````javascript runnable // make it pure using dependency injection: // take any impurities and make them a function parameter now we'll have 3 params: function logSomething(d, cnsl, foo) { const dt = d.toISOString(); cnsl.log(```${dt}: ${foo}\`\); return foo; }

// then we call it with the impure parts const foo = "make it pure using dependency injection!" const d = new Date\(\); logSomething\(d, console, foo\); // so yes! If you call it with those same parameters, it will return the same thing every single time. // and no external contact = pure. // That's the trick :\)

```text
***

<p>sum all values of the Array</p>

```javascript runnable
// forEach not nice :(
// forEach() is still a loop
const values = [1, 2, 3, 3, 5];
let sum = 0;
values.forEach( v => { sum += v; } ); // forEach() is still a loop
console.log( sum ); // 14
```

\`\`\`javascript runnable // Better do: // getting rid of loops const values = \[1, 2, 3, 3, 5\]; const sum = values.reduce\( \(acum, v\) =&gt; { const result = acum + v; return result; }, 0 \); console.log\( sum \); // 14

```text
Further information:
<a href="https://developer.mozilla.org/en/docs/Web/JavaScript/Reference/Global_Objects/Array/reduce">Array.prototype.reduce()</a>

***


### **Lazy functions**
Controlling the side-effect: **A side effect isn’t a side effect until it actually happens.**

```javascript runnable
// fZero() is impure
function fZero() { 
    console.log('IMPURE'); // IO log = Impure
    return 0;
}
```

\`\`\`javascript runnable // NOW returnZeroFunc\(\) is pure, the function does nothing other than return the same fZero function, every time. function returnZeroFunc\(\) { function fZero\(\) { // we wrapped fZero\(\) inside another function that just returned it right? console.log\('IMPURE'\); return 0; } return fZero; } // This function wrapping thing is a legitimate strategy. // We can keep hiding behind functions as long as we want. Oh yes! // And as long as we never actually call any of these functions, they’re all theoretically pure. // So, we control the side-effect: // Wrapping everything in a function lets us control those effects with precision. // We decide exactly when those side effects happen. const zeroFunc1 = returnZeroFunc\(\); // pure

```text
***

### **Variable Assignment**

```javascript runnablel
function doubleAndAddTen(x) {
    const doubled = x * 2;
    return doubled + 10;
}
```

\`\`\`javascript runnable // The doubled binding is now a function parameter, which doesn't modify the local scope for doubleAndAddTen. function doubleAndAddTen\(x\) { return \(doubled =&gt; doubled + 10\)\(x \* 2\); }

```text
> There are no variables in Functional Programming.

Stored values are still called variables because of history but they are constants, 
i.e. once x takes on a value, it’s that value for life. Don’t worry, x is usually a local variable so its life is usually short. 
But while it’s alive, it can never change.

***

### **Sequenced Side Effects**
```

// Impure console.log\('One'\); console.log\('Two'\);

```text

```

function pureLog\(msg\) { return \(\) =&gt; console.log\(msg\); }

const sideEffectSequence = \(firstEffect, secondEffect\) =&gt; \(\) =&gt; \(ignoredReturnValue =&gt; secondEffect\(\)\)\(firstEffect\(\)\);

const sequencedSideEffect = sideEffectSequence\(pureLog\('One'\), pureLog\('Two'\)\);

sequencedSideEffect\(\); // One, Two

\`\`\`

## **Bend your language to the problem, not the problem to the language**

The most obvios tip is: Please, take advantage of all the language features, if you have something that it is already done, well: use it. **Do not spend time working on languague problem, focus on bussiness goal issues.**

