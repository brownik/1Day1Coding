# Add Two Numbers

Last Updated: 2023년 8월 4일 오전 10:55
Difficulty: Medium
Resolved: true

링크 - [Add Two Numbers](https://leetcode.com/problems/add-two-numbers/description/)

**문제 설명**

You are given two **non-empty** linked lists representing two non-negative integers. The digits are stored in **reverse order**, and each of their nodes contains a single digit. Add the two numbers and return the sum as a linked list.

You may assume the two numbers do not contain any leading zero, except the number 0 itself.

**제한사항**

- The number of nodes in each linked list is in the range `[1, 100]`.
- `0 <= Node.val <= 9`
- It is guaranteed that the list represents a number that does not have leading zeros.

**입출력 예 #1**

![https://assets.leetcode.com/uploads/2020/10/02/addtwonumber1.jpg](https://assets.leetcode.com/uploads/2020/10/02/addtwonumber1.jpg)

```
Input: l1 = [2,4,3], l2 = [5,6,4]
Output: [7,0,8]
Explanation: 342 + 465 = 807.
```

**입출력 예 #2**

```
Input: l1 = [0], l2 = [0]
Output: [0]
```

**입출력 예 #3**

```
Input: l1 = [9,9,9,9,9,9,9], l2 = [9,9,9,9]
Output: [8,9,9,9,0,0,0,1]
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
    fun addTwoNumbers(l1: ListNode?, l2: ListNode?): ListNode? = checkAdd(l1, l2)
    fun checkAdd(l1: ListNode?, l2: ListNode?, add: Int = 0): ListNode? =
        when {
            l1 == null && l2 == null -> {
                if (add != 0) ListNode(add) else null
            }
            
            else -> {
                val sum = (l1?.`val` ?: 0) + (l2?.`val` ?: 0) + add
                val share = sum / 10
                val remainder = sum % 10
                val node = checkAdd(l1?.next, l2?.next, share)
                ListNode(remainder).apply { next = node }
            }
        }
}
```

3번 시도만에 풀었다…