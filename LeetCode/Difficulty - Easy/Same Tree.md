# Same Tree

Difficulty: Easy
Last Updated: 2023년 7월 6일 오후 5:37
Resolved: true

링크 - [Same Tree](https://leetcode.com/problems/same-tree/description/)

**문제 설명**

Given the roots of two binary trees `p` and `q`, write a function to check if they are the same or not.

Two binary trees are considered the same if they are structurally identical, and the nodes have the same value.

**제한사항**

- The number of nodes in both trees is in the range `[0, 100]`.
- `104 <= Node.val <= 104`

**입출력 예 #1**

![https://assets.leetcode.com/uploads/2020/12/20/ex1.jpg](https://assets.leetcode.com/uploads/2020/12/20/ex1.jpg)

```
Input: p = [1,2,3], q = [1,2,3]
Output: true
```

![https://assets.leetcode.com/uploads/2020/12/20/ex2.jpg](https://assets.leetcode.com/uploads/2020/12/20/ex2.jpg)

**입출력 예 #2**

```
Input: p = [1,2], q = [1,null,2]
Output: false
```

![https://assets.leetcode.com/uploads/2020/12/20/ex3.jpg](https://assets.leetcode.com/uploads/2020/12/20/ex3.jpg)

**입출력 예 #3**

```
Input: p = [1,2,1], q = [1,1,2]
Output: false
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
    fun isSameTree(p: TreeNode?, q: TreeNode?): Boolean =
        when {
            p == null && q == null -> true
            p == null -> false
            q == null -> false
            else -> q.`val` == p.`val` && isSameTree(p.left, q.left) && isSameTree(p.right, q.right)
        }
}
```