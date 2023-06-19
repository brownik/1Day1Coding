# Find the Highest Altitude

Difficulty: Easy
Last Updated: 2023년 6월 19일 오전 10:19
Resolved: true

링크 - [Find the Highest Altitude](https://leetcode.com/problems/find-the-highest-altitude/description/)

**문제 설명**

There is a biker going on a road trip. The road trip consists of `n + 1` points at different altitudes. The biker starts his trip on point `0` with altitude equal `0`.

You are given an integer array `gain` of length `n` where `gain[i]` is the **net gain in altitude** between points `i` and `i + 1` for all (`0 <= i < n)`. Return *the **highest altitude** of a point.*

**제한사항**

- `n == gain.length`
- `1 <= n <= 100`
- `100 <= gain[i] <= 100`

**입출력 예 #1**

```
Input: gain = [-5,1,5,0,-7]
Output: 1
Explanation: The altitudes are [0,-5,-4,1,1,-6]. The highest is 1.
```

**입출력 예 #2**

```
Input: gain = [-4,-3,-2,-1,4,3,2]
Output: 0
Explanation: The altitudes are [0,-4,-7,-9,-10,-6,-3,-1]. The highest is 0.
```

**풀이**

```kotlin
class Solution {
    fun largestAltitude(gain: IntArray): Int {
        var max = 0
        gain.fold(0) { t, n ->
            val result = t + n
            max = maxOf(max, result)
            result
        }
        return max
    }
}
```