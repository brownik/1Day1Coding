# k개의 수

Last Updated: 2023년 4월 17일 오후 10:48

링크 - [k개의 수](https://school.programmers.co.kr/learn/courses/30/lessons/120887)

**문제 설명**

1부터 13까지의 수에서, 1은 1, 10, 11, 12, 13 이렇게 총 6번 등장합니다. 정수 `i`, `j`, `k`가 매개변수로 주어질 때, `i`부터 `j`까지 `k`가 몇 번 등장하는지 return 하도록 solution 함수를 완성해주세요.

**제한사항**

- 1 ≤ `i` < `j` ≤ 100,000
- 0 ≤ `k` ≤ 9

**입출력 예**

| i | j | k | result |
| --- | --- | --- | --- |
| 1 | 13 | 1 | 6 |
| 10 | 50 | 5 | 5 |
| 3 | 10 | 2 | 0 |

**입출력 설명 #1**

- 본문과 동일합니다.

**입출력 설명 #2**

- 10부터 50까지 5는 15, 25, 35, 45, 50 총 5번 등장합니다. 따라서 5를 return 합니다.

**입출력 설명 #3**

- 3부터 10까지 2는 한 번도 등장하지 않으므로 0을 return 합니다.

**풀이#1**

```kotlin
class Solution {
    fun solution(i: Int, j: Int, k: Int): Int =
        List(j - i + 1) { i + it }.joinToString("").count { it == k.digitToChar() }
}
```

**풀이#2**

```kotlin
class Solution {
    fun solution(i: Int, j: Int, k: Int): Int {
        var answer = 0
        (i..j).forEach { num ->
            answer += num.toString().count { it == k.digitToChar() }
        }
        return answer
    }
}
```

효율성은 2번 코드가 더 낫다