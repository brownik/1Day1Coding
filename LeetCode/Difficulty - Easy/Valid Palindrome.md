# Valid Palindrome

Last Updated: 2023년 7월 11일 오후 6:15
Difficulty: Easy
Resolved: true

링크 - [Valid Palindrome](https://leetcode.com/problems/valid-palindrome/description/)

**문제 설명**

A phrase is a **palindrome** if, after converting all uppercase letters into lowercase letters and removing all non-alphanumeric characters, it reads the same forward and backward. Alphanumeric characters include letters and numbers.

Given a string `s`, return `true` *if it is a **palindrome**, or* `false` *otherwise*.

**제한사항**

- `1 <= s.length <= 2 * 105`
- `s` consists only of printable ASCII characters.

**입출력 예 #1**

```
Input: s = "A man, a plan, a canal: Panama"
Output: true
Explanation: "amanaplanacanalpanama" is a palindrome.
```

**입출력 예 #2**

```
Input: s = "race a car"
Output: false
Explanation: "raceacar" is not a palindrome.
```

**입출력 예 #3**

```
Input: s = " "
Output: true
Explanation: s is an empty string "" after removing non-alphanumeric characters.
Since an empty string reads the same forward and backward, it is a palindrome.
```

**풀이**

```kotlin
class Solution {
    fun isPalindrome(s: String): Boolean =
        s.toLowerCase().replace(Regex("""[^a-z|0-9]"""), "").let { it == it.reversed() }
}
```