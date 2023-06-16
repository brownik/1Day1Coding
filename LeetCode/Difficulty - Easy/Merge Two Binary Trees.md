# Merge Two Binary Trees

Difficulty: Easy
Last Updated: 2023년 6월 16일 오전 10:29
Resolved: true

링크 - [Merge Two Binary Trees](https://leetcode.com/problems/merge-two-binary-trees/)

**문제 설명**

You are given two binary trees `root1` and `root2`.

Imagine that when you put one of them to cover the other, some nodes of the two trees are overlapped while the others are not. You need to merge the two trees into a new binary tree. The merge rule is that if two nodes overlap, then sum node values up as the new value of the merged node. Otherwise, the NOT null node will be used as the node of the new tree.

Return *the merged tree*.

**Note:** The merging process must start from the root nodes of both trees.

**제한사항**

- The number of nodes in both trees is in the range `[0, 2000]`.
- `104 <= Node.val <= 104`

**입출력 예 #1**

![https://assets.leetcode.com/uploads/2021/02/05/merge.jpg](https://assets.leetcode.com/uploads/2021/02/05/merge.jpg)

```
Input: root1 = [1,3,2,5], root2 = [2,1,3,null,4,null,7]
Output: [3,4,5,5,4,null,7]
```

**입출력 예 #2**

```
Input: root1 = [1], root2 = [1,2]
Output: [2,2]
```

**풀이**

```kotlin
/**
 * Example:
 * var ti = TreeNode(5)
 * var v = ti.`val``
 * Definition for a binary tree node.
 * class TreeNode(var `val`: Int) {
 *     var left: TreeNode? = null
 *     var right: TreeNode? = null
 * }
 */
class Solution {
    fun mergeTrees(root1: TreeNode?, root2: TreeNode?): TreeNode? =
        when {
            root1 == null && root2 == null -> null
            root1 == null -> root2
            root2 == null -> root1
            else -> {
                val node = TreeNode(root1.`val` + root2.`val`)
                node.left = mergeTrees(root1.left, root2.left)
                node.right = mergeTrees(root1.right, root2.right)
                node
            }
        }
}
```