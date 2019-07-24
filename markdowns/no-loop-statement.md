## no-loop-statement: for, for...of, for...in, while, and do...while.

### no for

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


---
### no while-case

// instead of
```javascript
var day;
switch (new Date().getDay()) {
    case 0:
        day = "Sunday";
        break;
    case 1:
        day = "Monday";
        break;
    case 2:
        day = "Tuesday";
        break;
    case 3:
        day = "Wednesday";
        break;
    case 4:
        day = "Thursday";
        break;
    case 5:
        day = "Friday";
        break;
    case 6:
        day = "Saturday";
}
```


// better do
```javascript
const getDay = switchcase({
    0: 'Sunday',
    1: 'Monday',
    2: 'Tuesday',
    3: 'Wednesday',
    4: 'Thursday',
    5: 'Friday',
    6: 'Saturday'
  })('Unknown')
const getCurrentDay = () => 
  getDay(new Date().getDay())
const day = getCurrentDay()
```

LINK:
https://hackernoon.com/rethinking-javascript-eliminate-the-switch-statement-for-better-code-5c81c044716d

