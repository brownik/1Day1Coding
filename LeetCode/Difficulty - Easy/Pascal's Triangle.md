# Pascal’s Triangle

Difficulty: Easy
Last Updated: 2023년 7월 7일 오후 1:53
Resolved: true

링크 - [Pascal’s Triangle](https://leetcode.com/problems/pascals-triangle/description/)

**문제 설명**

Given an integer `numRows`, return the first numRows of **Pascal's triangle**.

In **Pascal's triangle**, each number is the sum of the two numbers directly above it as shown:

![https://upload.wikimedia.org/wikipedia/commons/0/0d/PascalTriangleAnimated2.gif](https://upload.wikimedia.org/wikipedia/commons/0/0d/PascalTriangleAnimated2.gif)

**제한사항**

- `1 <= numRows <= 30`

**입출력 예 #1**

```
Input: numRows = 5
Output: [[1],[1,1],[1,2,1],[1,3,3,1],[1,4,6,4,1]]
```

**입출력 예 #2**

```
Input: numRows = 1
Output: [[1]]
```

**풀이**

```kotlin
class Solution {
    fun generate(numRows: Int): List<List<Int>> {
        val answer = mutableListOf<List<Int>>()
        repeat(numRows) { i ->
            val list = mutableListOf<Int>()
            repeat(i + 1) { j ->
                list.add(
                    when (j) {
                        0, i -> 1
                        else -> answer[i - 1][j - 1] + answer[i - 1][j]
                    }
                )
            }
            answer.add(list)
        }
        return answer
    }
}
```