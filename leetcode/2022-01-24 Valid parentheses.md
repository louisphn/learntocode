# Valid Parentheses

Level: Easy

Given a string s containing just the characters '(', ')', '{', '}', '[' and ']', determine if the input string is valid.

An input string is valid if:

Open brackets must be closed by the same type of brackets.
Open brackets must be closed in the correct order.

**Example 1:**

```
Input: s = "()"
Output: true
```

**Example 2:**

```
Input: s = "()[]{}"
Output: true
```

**Example 3:**

```
Input: s = "(]"
Output: false
```

**Constraints:**

- 1 <= s.length <= 104
- s consists of parentheses only '()[]{}'.

<hr />

## Solution

Steps:

1.  Create valid parentheses hash map
2.  Create brackets stack, loop through string
3.  Check if current element is open bracket
4.  If it is open bracket, push to stack
5.  If it is not an open bracket, check if the last element in stack matches the valid parentheses with current element in string
6.  If it matches, pop the last element in stack
7.  If it does not match, return false
8.  Else loop to the end of an array, return true or false depends on stack length

```js
/**
 * @param {string} s
 * @return {boolean}
 */
const isValid = (s) => {
  // valid parentheses hashmap
  const validParentheses = {
    "]": "[",
    ")": "(",
    "}": "{",
  };
  // loop through string
  // if it is open bracket: push to stack
  // if it is not
  // if the value is equal to the key in hash map
  // pop stack
  // return false
  const stack = [];
  for (let i = 0; i < s.length; i += 1) {
    if (s[i] === "(" || s[i] === "[" || s[i] === "{") {
      stack.push(s[i]);
    } else if (stack[stack.length - 1] === validParentheses[s[i]]) {
      stack.pop();
    } else return false;
  }
  // check stack length
  return stack.length ? false : true;
};
```
