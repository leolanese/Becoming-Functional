## Immutable Update Utility Libraries

Because writing immutable update code can become tedious, there are a number of utility libraries that try to abstract out the process. These libraries vary in APIs and usage, but all try to provide a shorter and more succinct way of writing these updates. 
For example, Immer makes immutable updates a simple function and plain JavaScript objects:

```javascript
var usersState = [{ name: 'John Doe', address: { city: 'London' } }]
var newState = immer.produce(usersState, draftState => {
  draftState[0].name = 'Jon Doe'
  draftState[0].address.city = 'Paris'
  //nested update similar to mutable way
})
```

Some, like [dot-prop-immutable](https://github.com/kolodny/immutability-helper), take string paths for commands:

```javascript
state = dotProp.set(state, `todos.${index}.complete`, true)
```

Others, like [immutability-helper](https://github.com/kolodny/immutability-helper), use nested values and helper functions:

```javascript
var collection = [1, 2, { a: [12, 17, 15] }]
var newCollection = update(collection, {
  2: { a: { $splice: [[1, 1, 13, 14]] } }
})
```

They can provide a useful alternative to writing manual immutable update logic.

A list of many immutable update utilities can be found in the
[Immutable Data](https://github.com/markerikson/redux-ecosystem-links/blob/master/immutable-data.md#immutable-update-utilities)
