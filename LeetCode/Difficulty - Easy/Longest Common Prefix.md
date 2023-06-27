# Longest Common Prefix

Difficulty: Easy
Last Updated: 2023년 6월 27일 오후 4:06
Resolved: true

링크 - [Longest Common Prefix](https://leetcode.com/problems/longest-common-prefix/description/)

**문제 설명**

Write a function to find the longest common prefix string amongst an array of strings.

If there is no common prefix, return an empty string `""`.

**제한사항**

- `1 <= strs.length <= 200`
- `0 <= strs[i].length <= 200`
- `strs[i]` consists of only lowercase English letters.

**입출력 예 #1**

```
Input: strs = ["flower","flow","flight"]
Output: "fl"
```

**입출력 예 #2**

```
Input: strs = ["dog","racecar","car"]
Output: ""
Explanation: There is no common prefix among the input strings.
```

**풀이**

```kotlin
class Solution {
    fun longestCommonPrefix(strs: Array<String>): String {
        val answer = strs.first()
        answer.forEachIndexed { i, c ->
            if (strs.any { it.length == i || it[i] != c } ) return answer.substring(0, i)
        }
        return answer
    }
}
```