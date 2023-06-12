# Summary Ranges

Difficulty: Easy
Last Updated: 2023년 6월 12일 오후 2:03
Resolved: true

링크 - [Summary Ranges](https://leetcode.com/problems/summary-ranges/)

**문제 설명**

You are given a **sorted unique** integer array `nums`.

A **range** `[a,b]` is the set of all integers from `a` to `b` (inclusive).

Return *the **smallest sorted** list of ranges that **cover all the numbers in the array exactly***. That is, each element of `nums` is covered by exactly one of the ranges, and there is no integer `x` such that `x` is in one of the ranges but not in `nums`.

Each range `[a,b]` in the list should be output as:

- `"a->b"` if `a != b`
- `"a"` if `a == b`

**제한사항**

- `0 <= nums.length <= 20`
- `231 <= nums[i] <= 231 - 1`
- All the values of `nums` are **unique**.
- `nums` is sorted in ascending order.

**입출력 예 #1**

```
Input: nums = [0,1,2,4,5,7]
Output: ["0->2","4->5","7"]
Explanation: The ranges are:
[0,2] --> "0->2"
[4,5] --> "4->5"
[7,7] --> "7"
```

**입출력 예 #2**

```
Input: nums = [0,2,3,4,6,8,9]
Output: ["0","2->4","6","8->9"]
Explanation: The ranges are:
[0,0] --> "0"
[2,4] --> "2->4"
[6,6] --> "6"
[8,9] --> "8->9"
```

**풀이**

```kotlin
class Solution {
    fun summaryRanges(nums: IntArray): List<String> {
        val list = mutableListOf<String>()
        var start = 0
        For@ for (i in nums.indices) {
            when {
                start == i || nums[i - 1] + 1 == nums[i] -> continue@For
                start + 1 == i -> list.add(nums[start].toString())

                else -> list.add("${nums[start]}->${nums[i - 1]}")
            }
            start = i
        }
        when {
            nums.isEmpty() -> return emptyList()
            start == nums.size - 1 -> list.add(nums[start].toString())
            else -> list.add("${nums[start]}->${nums.last()}")
        }
        return list
    }
}
```