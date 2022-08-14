Level: Easy

Write a function to find the longest common prefix string amongst an array of strings.

If there is no common prefix, return an empty string "".

<hr />

#### Example 1:

```html
Input: strs = ["flower","flow","flight"] Output: "fl"
```

#### Example 2:

```html
Input: strs = ["dog","racecar","car"] Output: "" Explanation: There is no common
prefix among the input strings.
```

## Solution

```js
const longestCommonPrefix = (strs) => {
  if (!strs[0]) return "";
  if (strs.length === 1) return strs[0];
  let i = 0;
  while (strs[0][i] && strs.every((str) => str[i] === strs[0][i])) {
    i++;
  }
  return strs[0].substring(0, i);
};
```
