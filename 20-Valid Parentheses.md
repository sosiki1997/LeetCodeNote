## 题目描述

Given a string `s` containing just the characters `'('`, `')'`, `'{'`, `'}'`, `'['` and `']'`, determine if the input string is valid.

An input string is valid if:

1. Open brackets must be closed by the same type of brackets.
2. Open brackets must be closed in the correct order.
3. Every close bracket has a corresponding open bracket of the same type.

 

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

- `1 <= s.length <= 104`
- `s` consists of parentheses only `'()[]{}'`.

------

> 通常如果跟配对有关系，可以利用 stack(LIFO) 跟 hashmap 来解

## Hashmap 解法

#### Pyhton3

```python
class Solution:
    def isValid(self, s: str) -> bool:
        # 建立 Hashmap 和 stack
        lookup = {"(":")", "[":"]", "{":"}"}
        stack = []

        for char in s:
            if char in lookup:
                stack.append(char)
            elif not stack or char != lookup[stack.pop()]:
                return False
        return len(stack) == 0
```

执行用时：36 ms

内存消耗：15 MB
