# Do Declarative programming

> FP is a declarative paradigm, meaning that the program logic is expressed without explicitly describing the flow control. We abstract the flow control process

// instead of // Imperative/procedural Programming

```javascript
var array = [0, 1, 2, 3, 4, 5, 6, 7, 8, 9];
  for(let i = 0; i < array.length; i++) {
    array[i] = Math.pow(array[i], 2);
  }
array; //-> [0, 1, 4, 9, 16, 25, 36, 49, 64, 81]
```

// better do // ES6 & declarative & functional programming oriented

```javascript
[0, 1, 2, 3, 4, 5, 6, 7, 8, 9].map(num => Math.pow(num, 2));
```

// instead of // This example uses an IP style because, as we can see, it uses control flow statements

```javascript
interface Result {
 id: number;
 result:number;
}

const results: Result[] = [
 { id: 1, result: 64 },
 { id: 2, result: 87 },
 { id: 3, result: 89 }
];

function avg(arr: Result[]) {
 let total = 0;
 for (var i = 0; i < arr.length; i++) {
 total += arr[i].result;
 }
 return total / arr.length;
}

const resultsAvg = avg(results);
console.log(resultsAvg);
```

// better do 
// the following example is declarative because there are no control flow statements and there are no state mutations 
// resultsAvg is not reusable, but the add, addMany, div, mapProp, and avg functions they are.

```javascript
const add = (a: number, b: number) => a + b;
const addMany = (...args: number[]) => args.reduce(add, 0);
const div = (a: number, b: number) => a / b;
const mapProp = <T>(k: keyof T, arr: T[]) => arr.map(a => a[k]);
const avg = (arr: number[]) => div(addMany(...arr), arr.length);

interface Result {
    id: number;
    result:number;
}

const results: Result[] = [
    { id: 1, result: 64 },
    { id: 2, result: 87 },
    { id: 3, result: 89 }
];

const resultsAvg = avg(mapProp("result", results));
console.log(resultsAvg);
```

