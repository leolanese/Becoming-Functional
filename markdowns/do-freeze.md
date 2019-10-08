We need to avoid modify or add property in object, we have few libraries that can help us. 
We need to consider using freeze to prevent accidental mutations

## Consider using: ImmutableJS
"Inspired by inspired by Clojure, Scala, Haskell and other functional programming environments"
[ImmutableJS](https://immutable-js.github.io/immutable-js/)


## Consider deep-freeze:
Recursively Object.freeze() on objects and functions
[deep-freeze](https://github.com/substack/deep-freeze)


### Consider Immutability Helpers:
Mutate a copy of data without changing the original source
[Facebook Immutability helpers](https://github.com/kolodny/immutability-helper)
