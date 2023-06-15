# Root Equals Sum of Children

Difficulty: Easy
Last Updated: 2023년 6월 15일 오전 10:11
Resolved: true

링크 - [Root Equals Sum of Children](https://leetcode.com/problems/root-equals-sum-of-children/)

**문제 설명**

You are given the `root` of a **binary tree** that consists of exactly `3` nodes: the root, its left child, and its right child.

Return `true` *if the value of the root is equal to the **sum** of the values of its two children, or* `false` *otherwise*.

**제한사항**

- The tree consists only of the root, its left child, and its right child.
- `100 <= Node.val <= 100`

**입출력 예 #1**

![https://assets.leetcode.com/uploads/2022/04/08/graph3drawio.png](https://assets.leetcode.com/uploads/2022/04/08/graph3drawio.png)

```
Input: root = [10,4,6]
Output: true
Explanation: The values of the root, its left child, and its right child are 10, 4, and 6, respectively.
10 is equal to 4 + 6, so we return true.
```

**입출력 예 #2**

![https://assets.leetcode.com/uploads/2022/04/08/graph3drawio-1.png](https://assets.leetcode.com/uploads/2022/04/08/graph3drawio-1.png)

```
Input: root = [5,3,1]
Output: false
Explanation: The values of the root, its left child, and its right child are 5, 3, and 1, respectively.
5 is not equal to 3 + 1, so we return false.
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
    fun checkTree(root: TreeNode?): Boolean =
        root!!.`val` == root.right!!.`val` + root.left!!.`val`
}
```