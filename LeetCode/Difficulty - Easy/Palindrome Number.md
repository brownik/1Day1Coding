# Palindrome Number

Difficulty: Easy
Last Updated: 2023년 6월 26일 오후 5:50
Resolved: true

링크 - [Palindrome Number](https://leetcode.com/problems/palindrome-number/description/)

**문제 설명**

Given an integer x, return true *if* x *is a **palindrome**, and* false *otherwise*.

**Palindrome :** 

An integer is a **palindrome** when it reads the same forward and backward.

For example, `121` is a palindrome while `123` is not.

**제한사항**

- `-231 <= x <= 231 - 1`

**입출력 예 #1**

```
Input: x = 121
Output: true
Explanation: 121 reads as 121 from left to right and from right to left.
```

**입출력 예 #2**

```
Input: x = -121
Output: false
Explanation: From left to right, it reads -121. From right to left, it becomes 121-. Therefore it is not a palindrome.
```

**입출력 예 #3**

```
Input: x = 10
Output: false
Explanation: Reads 01 from right to left. Therefore it is not a palindrome.
```

**풀이**

```kotlin
class Solution {
    fun isPalindrome(x: Int): Boolean {
        var s = x.toString()
        while (s.length > 1) {
            if (s.first() == s.last()) {
                s = s.drop(1).dropLast(1)
            } else {
                return false
            }
        }
        return true
    }
}
```