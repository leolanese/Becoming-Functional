### no switch-case

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

---

// instead of
```javascript
switch("first") {
  case("first"):
    console.log("First Case")
  default:
    console.log("Default Case")
}
```

// better do: Object Literals
```javascript
const dogSwitch = (breed) => ({
  "border": "Border Collies are good boys and girls.",
  "pitbull": "Pit Bulls are good boys and girls.",
  "german": "German Shepherds are good boys and girls."
})[breed]
dogSwitch("border") // "Border Collies are good boys and girls."
```

LINK:
https://medium.com/chrisburgin/rewriting-javascript-replacing-the-switch-statement-cfff707cf045

---

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
const getCurrentDay = () => getDay(new Date().getDay())
const day = getCurrentDay()
```

LINK:
https://hackernoon.com/rethinking-javascript-eliminate-the-switch-statement-for-better-code-5c81c044716d

---

