# Single Number

Last Updated: 2023년 8월 3일 오후 6:02
Difficulty: Easy
Resolved: true

링크 - [Single Number](https://leetcode.com/problems/single-number/description/)

**문제 설명**

Given a **non-empty** array of integers `nums`, every element appears *twice* except for one. Find that single one.

You must implement a solution with a linear runtime complexity and use only constant extra space.

**제한사항**

- `1 <= nums.length <= 3 * 104`
- `3 * 104 <= nums[i] <= 3 * 104`
- Each element in the array appears twice except for one element which appears only once.

**입출력 예 #1**

```
Input: nums = [2,2,1]
Output: 1
```

**입출력 예 #2**

```
Input: nums = [4,1,2,1,2]
Output: 4
```

**입출력 예 #3**

```
Input: nums = [1]
Output: 1
```

**풀이**

```kotlin
class Solution {
    fun singleNumber(nums: IntArray): Int =
        nums.find { num -> nums.count { num == it } == 1 } ?: 0
}
```