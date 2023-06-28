# Find K Pairs with Smallest Sums

Difficulty: Medium
Last Updated: 2023년 6월 28일 오전 9:07
Resolved: true

링크 - [Find K Pairs with Smallest Sums](https://leetcode.com/problems/find-k-pairs-with-smallest-sums/description/)

**문제 설명**

You are given two integer arrays `nums1` and `nums2` sorted in **ascending order** and an integer `k`.

Define a pair `(u, v)` which consists of one element from the first array and one element from the second array.

Return *the* `k` *pairs* `(u1, v1), (u2, v2), ..., (uk, vk)` *with the smallest sums*.

**제한사항**

- `1 <= nums1.length, nums2.length <= 105`
- `109 <= nums1[i], nums2[i] <= 109`
- `nums1` and `nums2` both are sorted in **ascending order**.
- `1 <= k <= 104`

**입출력 예 #1**

```
Input: nums1 = [1,7,11], nums2 = [2,4,6], k = 3
Output: [[1,2],[1,4],[1,6]]
Explanation: The first 3 pairs are returned from the sequence: [1,2],[1,4],[1,6],[7,2],[7,4],[11,2],[7,6],[11,4],[11,6]
```

**입출력 예 #2**

```
Input: nums1 = [1,1,2], nums2 = [1,2,3], k = 2
Output: [[1,1],[1,1]]
Explanation: The first 2 pairs are returned from the sequence: [1,1],[1,1],[1,2],[2,1],[1,2],[2,2],[1,3],[1,3],[2,3]
```

**입출력 예 #3**

```
Input: nums1 = [1,2], nums2 = [3], k = 3
Output: [[1,3],[2,3]]
Explanation: All possible pairs are returned from the sequence: [1,3],[2,3]
```

**풀이**

```kotlin
class Solution {
    fun kSmallestPairs(nums1: IntArray, nums2: IntArray, k: Int): List<List<Int>> {
        val queue = PriorityQueue<Pair<Int, Int>>(compareBy { nums1[it.first] + nums2[it.second] })
        val result = arrayListOf<List<Int>>()
        queue.add(Pair(0, 0))
        while (result.size < k && queue.isNotEmpty()) {
            val (index1, index2) = queue.poll()!!
            result.add(listOf(nums1[index1], nums2[index2]))
            if (index2 + 1 < nums2.size) queue.offer(Pair(index1, index2 + 1))
            if (index2 == 0 && index1 + 1 < nums1.size) queue.offer(Pair(index1 + 1, 0))
        }
        return result
    }
}
```

처음 풀이를 할 때는 이중 for 문을 사용하여 각 원소의 합을 비교하며 result의 값을 교체해 주는 방법으로 했다. 교체해 주는 과정에서 result에 대해 sortedBy, indexOf와 같은 시간이 오래 걸리는 작업으로 인해 메모리 오류가 발생했다.

검색하여 알아본 결과 조건을 명시하면 자동으로 정렬을 해주는 PriorityQueue의 존재를 알게 되었다. 이를 사용하여 몇몇 과정을 생략을 하였고 해결할 수 있었다.

덤으로 kotlin에서도 collection을 이용해 변수를 한 번에 선언하는 방법을 알 수 있었다.