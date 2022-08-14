Sample array (from 1 to 20):

```js
const arr = [1, 2, 3, 4, 5, ..., 20]
```

Expected behavior:
Chunk it into different size chunks, yet with a simple pattern of: 4, 3, 3, 3, 4, 3, 3, 3

Expected result:

```js
[
  [
    // four
    1, 2, 3, 4,
  ],
  [
    // three (1/3)
    5, 6, 7,
  ],
  [
    // three (2/3)
    8, 9, 10,
  ],
  [
    // three (3/3)
    11, 12, 13,
  ],
  [
    // four
    14, 15, 16, 17,
  ],
  [
    // three (1/3)
    18, 19, 20,
  ], // and so on..
];
```

## Solutions

- [Reference](https://stackoverflow.com/questions/60231799/split-array-into-different-size-chunks-4-3-3-3-4-3-3-3-etc)

```js
const arr = Array.from({ length: 100 }, (_, i) => i);
const copy = [...arr];
const sizes = [4, 3, 3, 3];
const result = [];
let i = 0;
while (i <= arr.length && copy.length) {
  result.push(copy.splice(0, sizes[i % sizes.length]));
  i++;
}
console.log(result);
```
