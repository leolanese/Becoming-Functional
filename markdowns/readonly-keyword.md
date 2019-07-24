# readonly-keyword

You might think that using const would eliminate mutation from your TypeScript code. Wrong. Turns out that there's a pretty big loophole in const.

// instead of

```javascript
interface Foo {
  x: number;
  y: number;
}
const point: Foo = { x: 23, y: 44 };
point.x = 99; // change the deep values
```

// better do // It prevents you from assigning a value to the result of a member expression.

```javascript
interface Foo {
  readonly x: number;
  readonly y: number;
}
const point: Foo = { x: 23, y: 44 };
point.x = 99; // <- Now. No object mutation allowed.
```

// or even better // use ES2016 object spread

```javascript
interface Foo {
  readonly x: number;
  readonly y: number;
}
const foo: Foo = { x: 23, y: 44 };
const transformedPoint = { ...foo, x: 99 };
```

