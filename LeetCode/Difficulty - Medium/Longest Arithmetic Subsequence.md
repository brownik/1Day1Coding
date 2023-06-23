# Longest Arithmetic Subsequence

Difficulty: Medium
Last Updated: 2023년 6월 23일 오전 10:48
Resolved: true

링크 - [Longest Arithmetic Subsequence](https://leetcode.com/problems/longest-arithmetic-subsequence/description/)

**문제 설명**

Given an array `nums` of integers, return *the length of the longest arithmetic subsequence in* `nums`.

**Note** that:

- A **subsequence** is an array that can be derived from another array by deleting some or no elements without changing the order of the remaining elements.
- A sequence `seq` is arithmetic if `seq[i + 1] - seq[i]` are all the same value (for `0 <= i < seq.length - 1`).

**제한사항**

- `2 <= nums.length <= 1000`
- `0 <= nums[i] <= 500`

**입출력 예 #1**

```
Input: nums = [3,6,9,12]
Output: 4
Explanation:  The whole array is an arithmetic sequence with steps of length = 3.
```

**입출력 예 #2**

```
Input: nums = [9,4,7,2,10]
Output: 3
Explanation:  The longest arithmetic subsequence is [4,7,10].
```

**입출력 예 #3**

```
Input: nums = [20,1,15,3,10,5,8]
Output: 4
Explanation: The longest arithmetic subsequence is [20,15,10,5].
```

**풀이**

```kotlin
class Solution {
    fun longestArithSeqLength(nums: IntArray): Int {
        val list = Array<MutableMap<Int, Int>>(nums.size) { mutableMapOf() }
        var count = 0

        for (i in 1 until nums.size) {
            repeat(i) { j ->
                val diff = nums[i] - nums[j]
                list[i][diff] = (list[j][diff] ?: 1) + 1
                count = count.coerceAtLeast(list[i][diff] ?: 1)
            }
        }
        return count
    }
}
```

처음에는 nums[i +1] - nums[i] 값을 저장하고 비교하며 해보려고 했는데 계속해서 반복문만 늘어나 포기했다..

주어진 배열을 돌며 nums[i +1] - nums[i]가 동일하면 값만 +1을 해준다.

계속해서 return할 count값을 비교해주고 coerceAtLieast라는 api로 if문을 대신해주었다..