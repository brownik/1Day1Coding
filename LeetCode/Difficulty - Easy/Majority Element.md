# Majority Element

Last Updated: 2023년 7월 13일 오전 11:56
Difficulty: Easy
Resolved: true

링크 - [Majority Element](https://leetcode.com/problems/majority-element/description/)

**문제 설명**

Given an array `nums` of size `n`, return *the majority element*.

The majority element is the element that appears more than `⌊n / 2⌋` times. You may assume that the majority element always exists in the array.

**제한사항**

- `n == nums.length`
- `1 <= n <= 5 * 104`
- `109 <= nums[i] <= 109`

**입출력 예 #1**

```
Input: nums = [3,2,3]
Output: 3
```

**입출력 예 #2**

```
Input: nums = [2,2,1,1,1,2,2]
Output: 2
```

**풀이**

```kotlin
class Solution {
    fun majorityElement(nums: IntArray): Int {
        val numMap = mutableMapOf<Int, Int>()
        var answer = Pair(0, 0)
        nums.forEach { num ->
            numMap[num] = numMap[num]?.plus(1)  ?: 1
            if (numMap[num] == numMap[num]?.coerceAtLeast(answer.second)) answer = Pair(num, numMap[num]!!)
        }
        return answer.first
    }
}
```