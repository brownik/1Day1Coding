# Range Sum of BST

Difficulty: Easy
Last Updated: 2023년 6월 14일 오전 11:11
Resolved: true

링크 - [Range Sum of BST](https://leetcode.com/problems/range-sum-of-bst/)

**문제 설명**

Given the `root` node of a binary search tree and two integers `low` and `high`, return *the sum of values of all nodes with a value in the **inclusive** range* `[low, high]`.

**제한사항**

- `0 <= nums.length <= 20`
- `231 <= nums[i] <= 231 - 1`
- All the values of `nums` are **unique**.
- `nums` is sorted in ascending order.

**입출력 예 #1**

![https://assets.leetcode.com/uploads/2020/11/05/bst1.jpg](https://assets.leetcode.com/uploads/2020/11/05/bst1.jpg)

```
Input: root = [10,5,15,3,7,null,18], low = 7, high = 15
Output: 32
Explanation: Nodes 7, 10, and 15 are in the range [7, 15]. 7 + 10 + 15 = 32.
```

**입출력 예 #2**

![https://assets.leetcode.com/uploads/2020/11/05/bst2.jpg](https://assets.leetcode.com/uploads/2020/11/05/bst2.jpg)

```
Input: root = [10,5,15,3,7,13,18,1,null,6], low = 6, high = 10
Output: 23
Explanation: Nodes 6, 7, and 10 are in the range [6, 10]. 6 + 7 + 10 = 23.
```

**풀이**

```kotlin
/**
 * Example:
 * var ti = TreeNode(5)
 * var v = ti.`val`
 * Definition for a binary tree node.
 * class TreeNode(var `val`: Int) {
 *     var left: TreeNode? = null
 *     var right: TreeNode? = null
 * }
 */
class Solution {
    fun rangeSumBST(root: TreeNode?, low: Int, high: Int): Int =
        if (root == null) 0
        else (if (root.`val` in low..high) root.`val` else 0) +
                rangeSumBST(root.left, low, high) +
                rangeSumBST(root.right, low, high)
}
```

참고 : [https://jkroh.tistory.com/entry/LeetCode-938-Range-Sum-of-BST](https://jkroh.tistory.com/entry/LeetCode-938-Range-Sum-of-BST)

사실 내가 풀었다기보다 참고한 자바 코드로 동작 방식 확인하고 적용했다..

어렵다. 재귀. 그리고 트리.