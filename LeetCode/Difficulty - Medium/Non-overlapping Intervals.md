# Non-overlapping Intervals

Last Updated: 2023년 7월 19일 오후 2:47
Difficulty: Medium
Resolved: true

링크 - [Non-overlapping Intervals](https://leetcode.com/problems/non-overlapping-intervals/description/)

**문제 설명**

Given an array of intervals `intervals` where `intervals[i] = [starti, endi]`, return *the minimum number of intervals you need to remove to make the rest of the intervals non-overlapping*.

**제한사항**

- `1 <= intervals.length <= 105`
- `intervals[i].length == 2`
- `5 * 104 <= starti < endi <= 5 * 104`

**입출력 예 #1**

```
Input: intervals = [[1,2],[2,3],[3,4],[1,3]]
Output: 1
Explanation: [1,3] can be removed and the rest of the intervals are non-overlapping.
```

**입출력 예 #2**

```
Input: intervals = [[1,2],[1,2],[1,2]]
Output: 2
Explanation: You need to remove two [1,2] to make the rest of the intervals non-overlapping.
```

**입출력 예 #3**

```
Input: intervals = [[1,2],[2,3]]
Output: 0
Explanation: You don't need to remove any of the intervals since they're already non-overlapping.
```

**풀이**

```kotlin
class Solution {
    fun eraseOverlapIntervals(intervals: Array<IntArray>): Int {
        intervals.sortWith(compareBy { it[0] })
        var minValue = Integer.MIN_VALUE
        return intervals.count { (i, j) ->
            (minValue > i).apply {
                if (minValue <= i || minValue > j) minValue = j
            }
        }
    }
}
```