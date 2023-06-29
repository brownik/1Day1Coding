# Valid Parentheses

Difficulty: Easy
Last Updated: 2023년 6월 29일 오후 4:11
Resolved: true

링크 - [Valid Parentheses](https://leetcode.com/problems/valid-parentheses/description/)

**문제 설명**

Given a string `s` containing just the characters `'('`, `')'`, `'{'`, `'}'`, `'['` and `']'`, determine if the input string is valid.

An input string is valid if:

1. Open brackets must be closed by the same type of brackets.
2. Open brackets must be closed in the correct order.
3. Every close bracket has a corresponding open bracket of the same type.

**제한사항**

- `1 <= s.length <= 104`
- `s` consists of parentheses only `'()[]{}'`.

**입출력 예 #1**

```
Input: s = "()"
Output: true
```

**입출력 예 #2**

```
Input: s = "()[]{}"
Output: true
```

**입출력 예 #3**

```
Input: s = "(]"
Output: false
```

**풀이**

```kotlin
class Solution {
    fun isValid(s: String): Boolean {
        val map = mapOf('(' to ')', '[' to ']', '{' to '}')
        val newS = s.map { it }.toMutableList()
        val check = mutableListOf<Char>()
        if (s.length % 2 != 0) return false
        var i = 5
        while (newS.isNotEmpty() || check.isNotEmpty()) {
            when {
                newS.isEmpty() -> return false
                check.isEmpty() || map[newS.first()] != null -> {
                    check.add(newS.first())
                    newS.removeAt(0)
                }
                map[check.last()] == newS.first() -> {
                    newS.removeAt(0)
                    check.removeAt(check.size - 1)
                }
                else -> return false
            }
        }
        return true
    }
}
```