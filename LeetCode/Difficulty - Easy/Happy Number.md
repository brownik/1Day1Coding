# Happy Number

Last Updated: 2023년 7월 26일 오후 3:06
Difficulty: Easy
Resolved: true

링크 - [Happy Number](https://leetcode.com/problems/happy-number/description/)

**문제 설명**

Write an algorithm to determine if a number `n` is happy.

A **happy number** is a number defined by the following process:

- Starting with any positive integer, replace the number by the sum of the squares of its digits.
- Repeat the process until the number equals 1 (where it will stay), or it **loops endlessly in a cycle** which does not include 1.
- Those numbers for which this process **ends in 1** are happy.

Return `true` *if* `n` *is a happy number, and* `false` *if not*.

**제한사항**

- `1 <= n <= 231 - 1`

**입출력 예 #1**

```
Input: n = 19
Output: true
Explanation:
1^2 + 9^2 = 82
8^2 + 2^2 = 68
6^2 + 8^2 = 100
1^2 + 0^2 + 0^2 = 1
```

**입출력 예 #2**

```
Input: n = 2
Output: false
```

**풀이**

```kotlin
class Solution {
    fun isHappy(n: Int): Boolean {
        var sum = n
        var set = mutableSetOf<Int>()
        while (sum != 1) {
            var num = sum
            sum = 0
            while (num != 0) {
                sum += (num % 10) * (num % 10)
                num /= 10
            }
            if (set.contains(sum)) return false
            else set.add(sum)
        }
        return true
    }
}
```