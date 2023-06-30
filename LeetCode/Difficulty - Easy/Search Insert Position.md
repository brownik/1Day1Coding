# Search Insert Position

Difficulty: Easy
Last Updated: 2023년 6월 30일 오후 4:30
Resolved: true

링크 - [Search Insert Position](https://leetcode.com/problems/search-insert-position/description/)

**문제 설명**

Given a sorted array of distinct integers and a target value, return the index if the target is found. If not, return the index where it would be if it were inserted in order.

You must write an algorithm with `O(log n)` runtime complexity.

**제한사항**

- `1 <= nums.length <= 104`
- `104 <= nums[i] <= 104`
- `nums` contains **distinct** values sorted in **ascending** order.
- `104 <= target <= 104`

**입출력 예 #1**

```
Input: nums = [1,3,5,6], target = 5
Output: 2
```

**입출력 예 #2**

```
Input: nums = [1,3,5,6], target = 2
Output: 1
```

**입출력 예 #3**

```
Input: nums = [1,3,5,6], target = 7
Output: 4
```

**풀이**

```kotlin
class Solution {
    fun searchInsert(nums: IntArray, target: Int): Int =
        when {
            nums.last() < target -> nums.size
            nums.contains(target) -> nums.indexOf(target)
            else -> nums.indexOfFirst { it > target }
        }
}
```