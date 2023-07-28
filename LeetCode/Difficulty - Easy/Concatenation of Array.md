# Concatenation of Array

Last Updated: 2023년 7월 28일 오후 4:35
Difficulty: Easy
Resolved: true

링크 - [Concatenation of Array](https://leetcode.com/problems/concatenation-of-array/description/)

**문제 설명**

Given an integer array `nums` of length `n`, you want to create an array `ans` of length `2n` where `ans[i] == nums[i]` and `ans[i + n] == nums[i]` for `0 <= i < n` (**0-indexed**).

Specifically, `ans` is the **concatenation** of two `nums` arrays.

Return *the array* `ans`.

**제한사항**

- `n == nums.length`
- `1 <= n <= 1000`
- `1 <= nums[i] <= 1000`

**입출력 예 #1**

```
Input: nums = [1,2,1]
Output: [1,2,1,1,2,1]
Explanation: The array ans is formed as follows:
- ans = [nums[0],nums[1],nums[2],nums[0],nums[1],nums[2]]
- ans = [1,2,1,1,2,1]
```

**입출력 예 #2**

```
Input: nums = [1,3,2,1]
Output: [1,3,2,1,1,3,2,1]
Explanation: The array ans is formed as follows:
- ans = [nums[0],nums[1],nums[2],nums[3],nums[0],nums[1],nums[2],nums[3]]
- ans = [1,3,2,1,1,3,2,1]
```

**풀이**

```kotlin
class Solution {
    fun getConcatenation(nums: IntArray): IntArray =
        nums.let {
            val list = it.toMutableList()
            list.addAll(list)
            list.toIntArray()
        }
}
```