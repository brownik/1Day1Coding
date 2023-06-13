# Equal Row and Column Pairs

Difficulty: Medium
Last Updated: 2023년 6월 13일 오전 10:05
Resolved: true

링크 - [Equal Row and Column Pairs](https://leetcode.com/problems/equal-row-and-column-pairs/)

**문제 설명**

Given a **0-indexed** `n x n` integer matrix `grid`, *return the number of pairs* `(ri, cj)` *such that row* `ri` *and column* `cj` *are equal*.

A row and column pair is considered equal if they contain the same elements in the same order (i.e., an equal array).

**제한사항**

- `n == grid.length == grid[i].length`
- `1 <= n <= 200`
- `1 <= grid[i][j] <= 105`

**입출력 예 #1**

![https://assets.leetcode.com/uploads/2022/06/01/ex1.jpg](https://assets.leetcode.com/uploads/2022/06/01/ex1.jpg)

```
Input: grid = [[3,2,1],[1,7,6],[2,7,7]]
Output: 1
Explanation: There is 1 equal row and column pair:
- (Row 2, Column 1): [2,7,7]
```

**입출력 예 #2**

![https://assets.leetcode.com/uploads/2022/06/01/ex2.jpg](https://assets.leetcode.com/uploads/2022/06/01/ex2.jpg)

```
Input: grid = [[3,1,2,2],[1,4,4,5],[2,4,2,2],[2,4,2,2]]
Output: 3
Explanation: There are 3 equal row and column pairs:
- (Row 0, Column 0): [3,1,2,2]
- (Row 2, Column 2): [2,4,2,2]
- (Row 3, Column 2): [2,4,2,2]
```

**풀이**

```kotlin
class Solution {
    fun equalPairs(grid: Array<IntArray>): Int {
        var answer = 0
        val rows = grid.map { it.joinToString(",") }
        val columns = List(grid.first().size) { i ->
            List(grid.size) { j ->
                grid[j][i]
            }.joinToString(",")
        }
        columns.forEach { column ->
            answer += rows.count { it == column }
        }
        return answer
    }
}
```