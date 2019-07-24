# Avoid Shared State

'Shared state' is any variable, object, or memory space that exists in a shared scope, or as the property of an object
 being passed between scopes.

> FP avoids shared state, instead relying on immutable data structures and pure calculations.

```javascript
const x = {
  val: 2
};
const x1 = () => x.val += 1;
const x2 = () => x.val *= 2;
x1();
x2();
console.log(x.val); // 6 :)
```

// This example is exactly equivalent to the above, except...
```javascript
const y = {
  val: 2
};
const y1 = () => y.val += 1;
const y2 = () => y.val *= 2;
// the order of the function calls is reversed...
y2();
y1();
// which changes the resulting value:
console.log(y.val); // 5 :( 
```

### The problem?
With shared state is that in order to understand the effects of a function, you have to know the entire
history of every shared variable that the function uses or affects.


### Why?
The great benefit of pure functions is that their output is **deterministic** = 
**given an input it will always return the same value**. This characteristic makes them extremely easy to debug.

A common bug associated to 'share state' is **'race-condition'**:
```
 Your saveUser() function makes a request to an API on the server.
 While that’s happening, the user changes their profile picture with updateAvatar() and triggers another saveUser() request.
```

### Change order:
changing the order in which functions are called can cause a cascade of failures because functions which act on
shared state are timing dependent.

> With shared state, the order in which function calls are made changes the result of the function calls.

Further information:
https://stackoverflow.com/questions/34510/what-is-a-race-condition
