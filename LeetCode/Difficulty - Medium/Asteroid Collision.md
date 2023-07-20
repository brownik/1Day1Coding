# Asteroid Collision

Last Updated: 2023년 7월 20일 오후 5:44
Difficulty: Medium
Resolved: true

링크 - [Asteroid Collision](https://leetcode.com/problems/asteroid-collision/description/)

**문제 설명**

We are given an array `asteroids` of integers representing asteroids in a row.

For each asteroid, the absolute value represents its size, and the sign represents its direction (positive meaning right, negative meaning left). Each asteroid moves at the same speed.

Find out the state of the asteroids after all collisions. If two asteroids meet, the smaller one will explode. If both are the same size, both will explode. Two asteroids moving in the same direction will never meet.

**제한사항**

- `2 <= asteroids.length <= 104`
- `1000 <= asteroids[i] <= 1000`
- `asteroids[i] != 0`

**입출력 예 #1**

```
Input: asteroids = [5,10,-5]
Output: [5,10]
Explanation: The 10 and -5 collide resulting in 10. The 5 and 10 never collide.
```

**입출력 예 #2**

```
Input: asteroids = [8,-8]
Output: []
Explanation: The 8 and -8 collide exploding each other.
```

**입출력 예 #3**

```
Input: asteroids = [10,2,-5]
Output: [10]
Explanation: The 2 and -5 collide resulting in -5. The 10 and -5 collide resulting in 10
```

**풀이**

```kotlin
class Solution {
    fun asteroidCollision(asteroids: IntArray): IntArray {
        val queue: Deque<Int> = LinkedList()
        for (i in asteroids.indices) {
            while (queue.isNotEmpty() && asteroids[i] < 0 && queue.last > 0) {
                val diff = asteroids[i] + queue.last
                when {
                    diff < 0 -> queue.removeLast()
                    diff > 0 -> asteroids[i] = 0
                    else -> { asteroids[i] = 0; queue.removeLast() }
                }
            }
            if (asteroids[i] != 0) queue.addLast(asteroids[i])
        }
        return queue.toIntArray()
    }
}
```

요즘 들어 stack 관련 문제가 많이 나오는 듯..