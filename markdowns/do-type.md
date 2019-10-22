### Hindley-Milner

### The 'Type System':

Types are the meta language that enables people from all different backgrounds to communicate succinctly and effectively.
For the most part, they're written with a system called "Hindley-Milner".
<br/>
JS is a dynamic language. When working with pure functions, type signatures have an expressive power.These signatures are making
the function to shout what is expecting to recieve and to return exposing their behaviour and intention. 
<br/>
Types play an important part in FP. They are not only useful for compile time checks, but also turn out to be the best possible 
documentation available.
<br/>

```javascript
//   exp :: Number -> Number
const exp = (num) =>  num * num;

exp(2); // 4
```

#### This read: 
A function from Number to Number. In other words: A function that recieved a 'Number' and return a 'Number'.
<b>If this is a 'Pure Function' this 'Type System' declaration will remain for ever.</b>

### How you're going call?

There are type checking tools available for JavaScript such as [Flow](https://flow.org) or the typed dialect, TypeScript. 
Hindley-Milner type signatures can be found everywhere in the functional world. 
Adding also simplicity to 'read' and 'write' from any other developers from different backgrounds.

In typescript, you can create a type, not only for normal objects, but also for functions.

```javascript
type GenericFunction<ArgType> = (
   instance: ArgType,
   ...otherArgs: Array<any>
) => string

const func1: GenericFunction<Test> = (inst) => { 
  //code 
}

const func2: GenericFunction<Test2> = (inst, text:string) => {
  // more code 
}
```
