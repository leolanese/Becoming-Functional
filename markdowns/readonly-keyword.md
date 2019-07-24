### readonly-keyword

You might think that using const would eliminate mutation from your TypeScript code. Wrong. 
Turns out that there's a pretty big loophole in const.

// instead of
```javascript
interface Foo {
  x: number;
  y: number;
}
const point: Foo = { x: 23, y: 44 };
point.x = 99; // change the deep values
```

// better do
```javascript
interface Foo {
  readonly x: number;
  readonly y: number;
}
const point: Foo = { x: 23, y: 44 };
point.x = 99; // <- Now. No object mutation allowed.
```
It prevents you from assigning a value to the result of a member expression.
