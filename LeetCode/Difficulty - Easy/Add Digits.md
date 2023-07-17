# Add Digits

Last Updated: 2023년 7월 17일 오후 3:18
Difficulty: Easy
Resolved: true

링크 - [Add Digits](https://leetcode.com/problems/add-digits/description/)

**문제 설명**

Given an integer `num`, repeatedly add all its digits until the result has only one digit, and return it.

**제한사항**

- `0 <= num <= 231 - 1`

**입출력 예 #1**

```
Input: num = 38
Output: 2
Explanation: The process is
38 --> 3 + 8 --> 11
11 --> 1 + 1 --> 2 
Since 2 has only one digit, return it.
```

**입출력 예 #2**

```
Input: num = 0
Output: 0
```

**풀이**

```kotlin
class Solution {
    fun addDigits(num: Int): Int {
        var s = num
        var sum = 0
        while (s >= 10) {
            var check = s
            sum = 0
            while (check != 0)  {
                sum += check % 10
                check /= 10
            }
            s = sum
        }
        return s
    }
}
```