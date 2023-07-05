# Length of Last Word

Difficulty: Easy
Last Updated: 2023년 7월 5일 오후 3:02
Resolved: true

링크 - [Length of Last Word](https://leetcode.com/problems/length-of-last-word/description/)

**문제 설명**

Given a string `s` consisting of words and spaces, return *the length of the **last** word in the string.*

A **word** is a maximal substring consisting of non-space characters only.

**제한사항**

- `1 <= s.length <= 104`
- `s` consists of only English letters and spaces `' '`.
- There will be at least one word in `s`.

**입출력 예 #1**

```
Input: s = "Hello World"
Output: 5
Explanation: The last word is "World" with length 5.
```

**입출력 예 #2**

```
Input: s = "   fly me   to   the moon  "
Output: 4
Explanation: The last word is "moon" with length 4.
```

**입출력 예 #3**

```
Input: s = "luffy is still joyboy"
Output: 6
Explanation: The last word is "joyboy" with length 6.
```

**풀이**

```kotlin
class Solution {
    fun lengthOfLastWord(s: String): Int =
        s.split(Regex("""\s""")).last { it.isNotEmpty() }.length
}
```