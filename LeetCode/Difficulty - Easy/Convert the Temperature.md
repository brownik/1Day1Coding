# Convert the Temperature

Last Updated: 2023년 7월 27일 오후 2:02
Difficulty: Easy
Resolved: true

링크 - [Convert the Temperature](https://leetcode.com/problems/convert-the-temperature/description/)

**문제 설명**

You are given a non-negative floating point number rounded to two decimal places `celsius`, that denotes the **temperature in Celsius**.

You should convert Celsius into **Kelvin** and **Fahrenheit** and return it as an array `ans = [kelvin, fahrenheit]`.

Return *the array `ans`.* Answers within `10-5` of the actual answer will be accepted.

**Note that:**

- `Kelvin = Celsius + 273.15`
- `Fahrenheit = Celsius * 1.80 + 32.00`

**제한사항**

- `0 <= celsius <= 1000`

**입출력 예 #1**

```
Input: celsius = 36.50
Output: [309.65000,97.70000]
Explanation: Temperature at 36.50 Celsius converted in Kelvin is 309.65 and converted in Fahrenheit is 97.70.
```

**입출력 예 #2**

```
Input: celsius = 122.11
Output: [395.26000,251.79800]
Explanation: Temperature at 122.11 Celsius converted in Kelvin is 395.26 and converted in Fahrenheit is 251.798.
```

**풀이**

```kotlin
class Solution {
    fun convertTemperature(celsius: Double): DoubleArray =
        doubleArrayOf(
            celsius + 273.15,
            celsius * 1.80 + 32.00
        )
}
```