### Immutability. Avoid mutating state:

> It is important not to confuse **const**, with immutability.

### const
// we cannot assign nothing else to that object
// but we can change the content of the object
```javascript
const person = {
   name: "Leo"
};

person.name = "Tom"; 
console.log(person); // Tom
```

### Object.freeze
// we cannot change any value of the object once it’s frozen, it’s immutable
```javascript
const person = {
   name: "Leo"
};
Object.freeze(person);
person.name = "Tom"; 
console.log(person); // Leo
```

### deep.freeze
// The only problem is it isn’t deep freeze, only freeze the top level
```javascript
let person = {
   name: "Leonardo",
   profession: {
      name: "developer"
   }
};
Object.freeze(person);
person.profession.name = "hacker";
console.log(person); //output { name: 'Leo', profession: { name: 'hacker' } 
```

// solution:
Recursively Object.freeze() objects:
```javascript
// deepFreeze
function deepFreeze(object) {
   let propNames = Object.getOwnPropertyNames(object);
   for (let name of propNames) {
      let value = object[name];
      object[name] = value && typeof value === "object" ?  
                           deepFreeze(value) : value;
   }
   return Object.freeze(object);
}
let person = {
   name: "Leonardo",
   profession: {
      name: "developer"
   }
};

deepFreeze(person);

person.profession.name = "Hacker";

```
Funther information:
[npm deep-freeze](https://www.npmjs.com/package/deep-freeze)


Immutable objects never change: Avoid mutating state, avoids mutable data and side-effect

An immutable object is an object that can't be modified after it is created.
On the other side, a mutable object is any object which can be modified after it's created.

> Immutability is a central concept of functional programming because without it, the data flow in your program is lossy.

```
 const creates a variable name binding which can't be reassigned after creation.
 const does not create immutable objects.
```

JavaScript is not immutable by default, but you can write code that doesn't mutate variables.

---

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

