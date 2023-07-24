# Pow(x, n)

Last Updated: 2023년 7월 24일 오전 9:46
Difficulty: Medium
Resolved: true

링크 - [Pow(x, n)](https://leetcode.com/problems/powx-n/description/)

**문제 설명**

Implement [pow(x, n)](http://www.cplusplus.com/reference/valarray/pow/), which calculates `x` raised to the power `n` (i.e., `xn`).

**제한사항**

- `2 <= asteroids.length <= 104`
- `1000 <= asteroids[i] <= 1000`
- `asteroids[i] != 0`

**입출력 예 #1**

```
Input: x = 2.00000, n = 10
Output: 1024.00000
```

**입출력 예 #2**

```
Input: x = 2.10000, n = 3
Output: 9.26100
```

**입출력 예 #3**

```
Input: x = 2.00000, n = -2
Output: 0.25000
Explanation: 2-2 = 1/22 = 1/4 = 0.25
```

**풀이**

```kotlin
import kotlin.math.pow

class Solution {
    fun myPow(x: Double, n: Int): Double = x.pow(n)
}
```

..???