# Permutations

Last Updated: 2023년 8월 2일 오전 9:40
Difficulty: Medium
Resolved: true

링크 - [Permutations](https://leetcode.com/problems/permutations/description/)

**문제 설명**

Given an array `nums` of distinct integers, return *all the possible permutations*. You can return the answer in **any order**.

**제한사항**

- `1 <= nums.length <= 6`
- `10 <= nums[i] <= 10`
- All the integers of `nums` are **unique**.

**입출력 예 #1**

```
Input: nums = [1,2,3]
Output: [[1,2,3],[1,3,2],[2,1,3],[2,3,1],[3,1,2],[3,2,1]]
```

**입출력 예 #2**

```
Input: nums = [0,1]
Output: [[0,1],[1,0]]
```

**입출력 예 #3**

```
Input: nums = [1]
Output: [[1]]
```

**풀이**

```kotlin
class Solution {
    fun permute(nums: IntArray): List<List<Int>> =
        permutation(nums.toList())
    
    private fun <T> permutation(sub: List<T>, fin: List<T> = listOf()): List<List<T>> {
        return if(sub.isEmpty()) listOf(fin)
        else sub.flatMap { permutation(sub - it, fin + it) }
    }
}
```
