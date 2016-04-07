# birds-eye

> obj with nesting → collection containing all primitive value types and corresponding nest depths


## Install

```console
npm install --save birds-eye
```

## Usage

object with nesting:
```js
const obj = {
  a: 42,
  b: {},
  c: {
    d: 22,
    e: {
      f: 4
    }
  },
  g: {
    h: Math.E,
    i: (n) => n * n,
    j: {},
    k: {
      l: true,
      m: [],
      n: {
        o: {
          p: {
            q: 'Q'
          }
        },
        r: null
      },
      s: 42
    }
  },
  t: true
}
```

overview of nested structure of primitives:
```js
console.log(birdsEye(obj).structure);
// => 
[ { type: 'number', depth: 0 },
  { type: 'number', depth: 1 },
  { type: 'number', depth: 2 },
  { type: 'number', depth: 1 },
  { type: 'boolean', depth: 2 },
  { type: 'string', depth: 5 },
  { type: 'null', depth: 4 },
  { type: 'number', depth: 3 },
  { type: 'boolean', depth: 1 } ]
```

return all primitive types found at a given nest depth:
```js
console.log(birdsEye(obj).atDepth(1)); // => ['number', 'number', 'boolean']
console.log(birdsEye(obj).atDepth(5)); // => ['string']
console.log(birdsEye(obj).atDepth(42)); // => []
```
