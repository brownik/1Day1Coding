# Two Sum

Difficulty: Easy
Last Updated: 2023년 6월 21일 오후 5:21
Resolved: true

```
Input: nums = [2,7,11,15], target = 9
Output: [0,1]
Explanation: Because nums[0] + nums[1] == 9, we return [0, 1].
```

링크 - [Two Sum](https://leetcode.com/problems/two-sum/description/)

**문제 설명**

Given an array of integers `nums` and an integer `target`, return *indices of the two numbers such that they add up to `target`*.

You may assume that each input would have ***exactly* one solution**, and you may not use the *same* element twice.

You can return the answer in any order.

**제한사항**

- `2 <= nums.length <= 104`
- `109 <= nums[i] <= 109`
- `109 <= target <= 109`
- **Only one valid answer exists.**

**입출력 예 #1**

```
Input: nums = [2,7,11,15], target = 9
Output: [0,1]
Explanation: Because nums[0] + nums[1] == 9, we return [0, 1].
```

**입출력 예 #2**

```
Input: nums = [3,2,4], target = 6
Output: [1,2]
```

**입출력 예 #3**

```
Input: nums = [3,3], target = 6
Output: [0,1]
```

**풀이**

```kotlin
class Solution {
    fun twoSum(nums: IntArray, target: Int): IntArray {
        val result = mutableListOf<Int>()
        for (i in nums.indices) {
            val otherNum = target - nums[i]
            val otherIndex = nums.indexOfLast { it == otherNum }
            if (i != otherIndex && nums.contains(otherNum)) {
                result.add(i)
                result.add(otherIndex)
                break
            }
        }
        return result.toIntArray()
    }
}
```