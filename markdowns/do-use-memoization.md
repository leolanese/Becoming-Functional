# Memoization

// a simple memoize function that takes in a function
// and returns a memoized function
```javascript
const memoize = (fn) => {
  let cache = {};
  return (...args) => {
    let n = args[0];  // just taking one argument here
    if (n in cache) { // check cache!
      console.log('Fetching from cache');
      return cache[n];
    } else {
      console.log('Calculating result');
      let result = fn(n);
      cache[n] = result; // to the cache!
      return result;
    }
  }
}


// memoize call
const squareNumber = memoize(x => x * x);

// Calculating result
squareNumber(4); // 16

// Fetching from cache <-- :)
squareNumber(4); // 16

// Fetching from cache
squareNumber(4); // 16
```

When to memoize your functions:
In order to memoize a function, it should be pure so that return values are the same for same inputs every time.


## Where to memoize your functions:

### API calls:
It might look like you should memoize your 'API calls' however it isn’t necessary because the browser automatically caches them for you.

@ngrx/store selector: <br>
-Selectors are pure functions.
-Selectors are methods used for obtaining slices of store state.
-@ngrx/store provides a few helper functions for optimizing this selection.


### When using the:

Inside out inside our ../reducer/index.ts

'createSelector' and 'createFeatureSelector'

functions @ngrx/store keeps track of the latest arguments in which your selector function was invoked.
Because selectors are pure functions, the last result can be returned when the arguments match without reinvoking your selector function.
This can provide performance benefits, particularly with selectors that perform expensive computation.

Selectors are memoized functions used to compute derived values from the store.
Being memoized implies values are only computed when the inputs to the selector function change.
