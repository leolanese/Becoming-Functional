# Do Declarative programming

- FP is a declarative paradigm software development style, like IP or OOP, thats keeps 'functions' and 'data' separated.
- Separate this long function into shorter functions, each with a single purpose.


// instead of use Imperative Programming
```javascript
var arr = [1, 2, 3, 4, 5];
function odds(arr) {
  var result = [];
  for (let i = 0; i < arr.length; i++) {
    var item = arr[i];
    if (i % 2 === 0) {
      result.push(item);
    }
  }
  return result;
}
odds(arr); // [1, 3, 5]
```

// better do Procedural Programming <br />
```javascript
const arr = [1, 2, 3, 4, 5];
const odds = arr => arr.filter(item => item % 2 !== 0);
odds(arr); // [1, 3, 5]
```

---

// instead of use Imperative Programming <br />
```javascript
var array = [0, 1, 2, 3, 4, 5, 6, 7, 8, 9];
  for(let i = 0; i < array.length; i++) {
    array[i] = Math.pow(array[i], 2);
  }
array; //-> [0, 1, 4, 9, 16, 25, 36, 49, 64, 81]
```

// better do procedural Programming <br />
// ES6 & declarative & functional programming oriented <br />

```javascript
[0, 1, 2, 3, 4, 5, 6, 7, 8, 9].map(num => Math.pow(num, 2));
```

// instead of <br />
// This example uses an IP style because, as we can see, it uses control flow statements<br />

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

// better do <br />
// the following example is declarative because there are no control flow statements and there are no state mutations <br />
// resultsAvg is not reusable, but the add, addMany, div, mapProp, and avg functions they are.<br />

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

