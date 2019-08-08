## ES6 Rest operators


// instead of
```javascript
const newObj = {
  'atr1': 1,
  'atr2': 2
}
if (1 === 1) {
  newObj['atr3'] = 3
}
console.log(newObj); {atr1: 1, atr2: 2, atr3: 3}
```

// better do
```javascript
betterDo = (condition, object) => condition 
                    ? object
                    : {};                                      
newObject = {
  'atr1': 1,
  'atr2': 2,
  ...betterDo(1 === 1, {'atr3': 3})
}; // {atr1: 1, atr2: 2, atr3: 3}                                 
```
