# Implement strStr()

Level: Easy

Return the index of the first occurrence of needle in haystack, or -1 if needle is not part of haystack.

Clarification:

What should we return when needle is an empty string? This is a great question to ask during an interview.

For the purpose of this problem, we will return 0 when needle is an empty string. This is consistent to C's strstr() and Java's indexOf().

<hr />

#### Example 1:

```html
Input: haystack = "hello", needle = "ll" Output: 2
```

#### Example 2:

```html
Input: haystack = "aaaaa", needle = "bba" Output: -1
```

#### Example 3:

```html
Input: haystack = "", needle = "" Output: 0
```

### Constraints:

- 0 <= haystack.length, needle.length <= 5 \* 104
- haystack and needle consist of only lower-case English characters.

## Solution

```js
const strStr = (haystack, needle) => {
  if (needle.length === 0) return 0;
  if (needle === haystack) return 0;
  // haystack.length - needle.length is the last index where we can find needle in haystack
  for (let i = 0; i <= haystack.length - needle.length; i++) {
    if (needle === haystack.substring(i, i + needle.length)) {
      return i;
    }
  }

  return -1;
};
```
