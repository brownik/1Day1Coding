# Search in Rotated Sorted Array

Last Updated: 2023년 8월 8일 오후 2:05
Difficulty: Medium
Resolved: true

링크 - [Search in Rotated Sorted Array](https://leetcode.com/problems/search-in-rotated-sorted-array/description/)

**문제 설명**

There is an integer array `nums` sorted in ascending order (with **distinct** values).

Prior to being passed to your function, `nums` is **possibly rotated** at an unknown pivot index `k` (`1 <= k < nums.length`) such that the resulting array is `[nums[k], nums[k+1], ..., nums[n-1], nums[0], nums[1], ..., nums[k-1]]` (**0-indexed**). For example, `[0,1,2,4,5,6,7]` might be rotated at pivot index `3` and become `[4,5,6,7,0,1,2]`.

Given the array `nums` **after** the possible rotation and an integer `target`, return *the index of* `target` *if it is in* `nums`*, or* `-1` *if it is not in* `nums`.

You must write an algorithm with `O(log n)` runtime complexity.

**제한사항**

- 
- `1 <= nums.length <= 5000`
- `10^4 <= nums[i] <= 10^4`
- All values of `nums` are **unique**.
- `nums` is an ascending array that is possibly rotated.
- `10^4 <= target <= 10^4`

**입출력 예 #1**

```
Input: nums = [4,5,6,7,0,1,2], target = 0
Output: 4
```

**입출력 예 #2**

```
Input: nums = [4,5,6,7,0,1,2], target = 3
Output: -1
```

**입출력 예 #3**

```
Input: nums = [1], target = 0
Output: -1
```

**풀이**

```kotlin
class Solution {
    fun search(nums: IntArray, target: Int): Int = nums.indexOf(target)
}
```