### no switch-case


// instead of
```javascript
var color = 'black';
switch (color) {
    case "black":
        alert('black')
        break;
    case "green":
        alert('green')
        break;
    case "red":
        alert('red')
        break;
    case "blue":
        alert('blue')
        break;
    case "white":
        alert('white')
        break;
    default:
        alert('no color')
}; // alert('black')
```

// better do: From Procedural Programming to OOP + FE using an object literal approach
```javascript
const black = () => alert('black');
const red = () => alert('red');
const blue = () => alert('blue');
const green = () => alert('green');

function getColor(type) {
  const colors = {
    'black': black,
    'red': red,
    'blue': blue,
    'green': green,
    'default': function(){alert('no color')}
  };
  return (colors[type] || colors['default'])();
}
getColor('black'); // alert('black')
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

