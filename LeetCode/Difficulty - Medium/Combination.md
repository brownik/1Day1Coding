# Combination

Last Updated: 2023년 8월 1일 오후 8:37
Difficulty: Medium
Resolved: true

링크 - [Combination](https://leetcode.com/problems/combinations/)

**문제 설명**

Given two integers `n` and `k`, return *all possible combinations of* `k` *numbers chosen from the range* `[1, n]`.

You may return the answer in **any order**.

**제한사항**

- `1 <= n <= 20`
- `1 <= k <= n`

**입출력 예 #1**

```
Input: n = 4, k = 2
Output: [[1,2],[1,3],[1,4],[2,3],[2,4],[3,4]]
Explanation: There are 4 choose 2 = 6 total combinations.
Note that combinations are unordered, i.e., [1,2] and [2,1] are considered to be the same combination.
```

**입출력 예 #2**

```
Input: n = 1, k = 1
Output: [[1]]
Explanation: There is 1 choose 1 = 1 total combination.
```

**풀이**

```kotlin
class Solution {
    fun combine(n: Int, k: Int): List<List<Int>> {
        val sample = (1..n).toList()
        val set = mutableSetOf<List<Int>>()
        combination(element = sample, limit = k).forEach { set.add(it) }
        return set.toList()
    }

    private fun <T> combination(
        element: List<T>,
        limit: Int = element.size,
        fin: List<T> = listOf(),
        index: Int = 0
    ): List<List<T>> {
        return if (fin.size >= limit) {
            listOf(fin)
        } else {
            element.slice(index until element.size).flatMapIndexed { i: Int, t: T ->
                combination(element, limit, fin + t, index + i + 1)
            }
        }
    }
}
```

맞는 풀이다.. 다만 Leetcode의 kotlin 버전이 너무너무너무 낮다.. 업데이트 좀 해주라…