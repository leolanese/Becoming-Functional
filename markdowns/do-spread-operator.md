## Spread operator Immutable object update

Object spread is convenient to modify objects in an immutable manner.

```javascript
const book = {
  name: 'JavaScript: The Definitive Guide',
  author: 'David Flanagan',
  edition: 5,
  year: 2008
};

const newerBook = {
  ...book,
  edition: 6,  // <----- Overwrites book.edition
  year: 2011   // <----- Overwrites book.year
};

console.log(newerBook);
/*
{
  name: 'JavaScript: The Definitive Guide',
  author: 'David Flanagan',
  edition: 6,
  year: 2011
}
*/
```

