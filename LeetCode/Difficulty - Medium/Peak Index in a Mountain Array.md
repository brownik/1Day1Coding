# Peak Index in a Mountain Array

Last Updated: 2023년 7월 25일 오후 1:37
Difficulty: Medium
Resolved: true

링크 - [Peak Index in a Mountain Array](https://leetcode.com/problems/peak-index-in-a-mountain-array/description/)

**문제 설명**

An array `arr` a **mountain** if the following properties hold:

- `arr.length >= 3`
- There exists some `i` with `0 < i < arr.length - 1` such that:
    - `arr[0] < arr[1] < ... < arr[i - 1] < arr[i]`
    - `arr[i] > arr[i + 1] > ... > arr[arr.length - 1]`

Given a mountain array `arr`, return the index `i` such that `arr[0] < arr[1] < ... < arr[i - 1] < arr[i] > arr[i + 1] > ... > arr[arr.length - 1]`.

You must solve it in `O(log(arr.length))` time complexity.

**제한사항**

- `3 <= arr.length <= 105`
- `0 <= arr[i] <= 106`
- `arr` is **guaranteed** to be a mountain array.

**입출력 예 #1**

```
Input: arr = [0,1,0]
Output: 1
```

**입출력 예 #2**

```
Input: arr = [0,2,1,0]
Output: 1
```

**입출력 예 #3**

```
Input: arr = [0,10,5,2]
Output: 1
```

**풀이 #1**

```kotlin
class Solution {
    fun peakIndexInMountainArray(arr: IntArray): Int = arr.indexOf(arr.sorted().last())
}
```

**풀이 #2**

```kotlin
class Solution {
    fun peakIndexInMountainArray(arr: IntArray): Int {
        var max = Integer.MIN_VALUE
        var answer = 0
        arr.forEachIndexed { i, n ->
            val num = max.coerceAtLeast(n)
            if (num != max) {
                max = num
                answer = i
            }
        }
        return answer
    }
}
```