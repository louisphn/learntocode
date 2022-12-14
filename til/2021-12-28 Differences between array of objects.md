# Differences between array of objects

Get the difference between two arrays of objects in Javascript one liner snippet:

```js
const arrayOne = [
  { value: "4a55eff3-1e0d-4a81-9105-3ddd7521d642", display: "Jamsheer" },
  { value: "644838b3-604d-4899-8b78-09e4799f586f", display: "Muhammed" },
  { value: "b6ee537a-375c-45bd-b9d4-4dd84a75041d", display: "Ravi" },
  { value: "e97339e1-939d-47ab-974c-1b68c9cfb536", display: "Ajmal" },
  { value: "a63a6f77-c637-454e-abf2-dfb9b543af6c", display: "Ryan" },
];

const arrayTwo = [
  { value: "4a55eff3-1e0d-4a81-9105-3ddd7521d642", display: "Jamsheer" },
  { value: "644838b3-604d-4899-8b78-09e4799f586f", display: "Muhammed" },
  { value: "b6ee537a-375c-45bd-b9d4-4dd84a75041d", display: "Ravi" },
  { value: "e97339e1-939d-47ab-974c-1b68c9cfb536", display: "Ajmal" },
];
```

```js
const results = arrayOne.filter(
  ({ value: id1 }) => !arrayTwo.some(({ value: id2 }) => id2 === id1)
);
```

#### Result:

```js
console.log(results);
// console
[
  {
    value: "a63a6f77-c637-454e-abf2-dfb9b543af6c",
    display: "Ryan",
  },
];
```
