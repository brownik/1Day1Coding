# Merge Two Sorted Lists

Last Updated: 2023년 8월 9일 오후 1:15
Difficulty: Easy
Resolved: true

링크 - [Merge Two Sorted Lists](https://leetcode.com/problems/merge-two-sorted-lists/description/)

**문제 설명**

You are given the heads of two sorted linked lists `list1` and `list2`.

Merge the two lists into one **sorted** list. The list should be made by splicing together the nodes of the first two lists.

Return *the head of the merged linked list*.

**제한사항**

- The number of nodes in both lists is in the range `[0, 50]`.
- `100 <= Node.val <= 100`
- Both `list1` and `list2` are sorted in **non-decreasing** order.

**입출력 예 #1**

![https://assets.leetcode.com/uploads/2020/10/03/merge_ex1.jpg](https://assets.leetcode.com/uploads/2020/10/03/merge_ex1.jpg)

```
Input: list1 = [1,2,4], list2 = [1,3,4]
Output: [1,1,2,3,4,4]
```

**입출력 예 #2**

```
Input: list1 = [], list2 = []
Output: []
```

**입출력 예 #3**

```
Input: list1 = [], list2 = [0]
Output: [0]
```

**풀이**

```kotlin
/**
 * Example:
 * var li = ListNode(5)
 * var v = li.`val`
 * Definition for singly-linked list.
 * class ListNode(var `val`: Int) {
 *     var next: ListNode? = null
 * }
 */
class Solution {
    fun mergeTwoLists(list1: ListNode?, list2: ListNode?): ListNode? =
        checkNode(list1, list2)

    private fun checkNode(l1: ListNode?, l2: ListNode?): ListNode? =
        when {
            l1 == null && l2 == null -> null
            else -> {
                val num1 = l1?.`val` ?: Integer.MAX_VALUE
                val num2 = l2?.`val` ?: Integer.MAX_VALUE
                val node = if (num1 <= num2) checkNode(l1?.next, l2)
                else checkNode(l1, l2?.next)
                ListNode(minOf(num1, num2)).apply { next = node }
            }
        }
}
```