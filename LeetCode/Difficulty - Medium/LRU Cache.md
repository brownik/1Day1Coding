# LRU Cache

Last Updated: 2023년 7월 18일 오후 1:12
Difficulty: Medium
Resolved: true

링크 - [LRU Cache](https://leetcode.com/problems/lru-cache/description/)

**문제 설명**

Design a data structure that follows the constraints of a **[Least Recently Used (LRU) cache](https://en.wikipedia.org/wiki/Cache_replacement_policies#LRU)**.

Implement the `LRUCache` class:

- `LRUCache(int capacity)` Initialize the LRU cache with **positive** size `capacity`.
- `int get(int key)` Return the value of the `key` if the key exists, otherwise return `1`.
- `void put(int key, int value)` Update the value of the `key` if the `key` exists. Otherwise, add the `key-value` pair to the cache. If the number of keys exceeds the `capacity` from this operation, **evict** the least recently used key.

The functions `get` and `put` must each run in `O(1)` average time complexity.

**제한사항**

- `1 <= capacity <= 3000`
- `0 <= key <= 104`
- `0 <= value <= 105`
- At most `2 * 105` calls will be made to `get` and `put`.

**입출력 예 #1**

```
Input
["LRUCache", "put", "put", "get", "put", "get", "put", "get", "get", "get"]
[[2], [1, 1], [2, 2], [1], [3, 3], [2], [4, 4], [1], [3], [4]]
Output
[null, null, null, 1, null, -1, null, -1, 3, 4]

Explanation
LRUCache lRUCache = new LRUCache(2);
lRUCache.put(1, 1); // cache is {1=1}
lRUCache.put(2, 2); // cache is {1=1, 2=2}
lRUCache.get(1);    // return 1
lRUCache.put(3, 3); // LRU key was 2, evicts key 2, cache is {1=1, 3=3}
lRUCache.get(2);    // returns -1 (not found)
lRUCache.put(4, 4); // LRU key was 1, evicts key 1, cache is {4=4, 3=3}
lRUCache.get(1);    // return -1 (not found)
lRUCache.get(3);    // return 3
lRUCache.get(4);    // return 4
```

**풀이**

```kotlin
class LRUCache(private val capacity: Int) {

    val map = mutableMapOf<Int, Int>()
    private var order: Deque<Int> = LinkedList()

    fun get(key: Int): Int {
        order.remove(key)
        if (map.containsKey(key)) order.addLast(key)
        return map[key] ?: -1
    }

    fun put(key: Int, value: Int) {
        order.remove(key)
        map[key] = value
        order.addLast(key)
        if (map.size > capacity) {
            val recent = order.pollFirst()
            recent?.let { map.remove(it) }
        }
    }
}

/**
 * Your LRUCache object will be instantiated and called as such:
 * var obj = LRUCache(capacity)
 * var param_1 = obj.get(key)
 * obj.put(key,value)
 */
```

사실 문제가 너무 이해가 안돼서 문제 이해하는 데만 30분은 걸린 것 같다..

정리하자면…

1. get 할 때는 map에 있으면 key값의 value를 없다면 -1을 반환
2. put, get 함수가 실행될 때의 key값을 가장 최근에 사용된 값으로 갱신
3. put할 때 capacity 보다 map의 size가 크다면 가장 이전에 사용된 값을 제거 후 put

위의 내용대로만 하면 될 것 같다..!