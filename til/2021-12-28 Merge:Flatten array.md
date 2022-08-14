Use to merge nested array or multiple arrays:

Sample array:

```js
const arrays = [["$6"], ["$12"], ["$25"], ["$25"], ["$18"], ["$22"], ["$10"]];
```

Expected result:

```js
const merged = ["$6", "$12", "$25", ...]
```

## Solutions

- Use `apply` method:

```js
const merged = [].concat.apply([], arrays);
```

- Use `flat` method:
  Reference: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/flat

```js
const merged = arrays.flat();
```
