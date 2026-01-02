---
title: ⚙️ 유클리드 호제법(최대공약수)
date: 2025-02-04 00:45 +0900
last_modified_at: 2025-02-05 23:13 +0900
categories: [알고리즘]
tags: [알고리즘, 개념]
image: /assets/blog-images/posts/2025-02-04-gcd-euclidean-algorithm/title.png
---

> **유클리드 호제법**: 기원전 3세기 경의 수학자 유클리드가 만든 **최대공약수**를 구하는 알고리즘이다. 유클리드 호제법은 두 수의 최대공약수를 구할 때, 큰 수를 작은 수로 나누고 나머지를 반복적으로 대체하여 계산한다.

## 1. 유클리드 호제법이 필요한 이유

a, b 두 개의 숫자가 있을 때 유클리드 알고리즘 없이 최대공약수를 구하는 방법은 다음과 같다.  
a와 b 중 작은 숫자를 시작으로 두 수를 나누어 본다. 숫자를 하나씩 줄여나가 1이 될 때까지 나눠 보다가 둘 다 나누어떨어지는 숫자가 최대공약수가 된다.

이 경우 최악의 경우 `min(a, b)` 번의 반복이 필요하다. `O(N)` 시간 복잡도를 가진다.

```kotlin
import kotlin.math.min

fun gcdBruteForce(a: Int, b: Int): Int {
    val min = min(a, b)
    for(i in min downTo 1) {
        if(a % i == 0 && b % i == 0) {
            return i
        }
    }
    return 1
}

fun main() {
    println(gcdBruteForce(48, 18)) // 6
}
```

## 2. 유클리드 호제법

### ✨ 유클리드 호제법 순서

1. 두 수 중 큰 수를 작은 수로 나눈다.
2. 나머지가 0이면 작은 수가 최대공약수가 된다.
3. 나머지가 0이 아니면 작은 수가 큰 수가 되고, 나머지를 작은 수로 대체하고 1단계로 돌아간다.

### 반복문 방식

```kotlin
fun gcdIterative(a: Int, b: Int): Int {
    var x = a
    var y = b
    while(y != 0) {
        val temp = x % y
        x = y
        y = temp
    }
    return x
}

fun main() {
    println(gcdIterative(48, 18)) // 6
}
```

### 재귀 방식

```kotlin
fun gcdRecursive(a: Int, b: Int): Int {
    return if(b == 0) a else gcdRecursive(b, a % b)
}

fun main() {
    println(gcdRecursive(48, 18)) // 6
}
```

### 반복문 vs 재귀의 차이점

| 방식   | 코드 길이     | 가독성             | 성능                                   |
| :----- | :------------ | :----------------- | :------------------------------------- |
| 반복문 | 상대적으로 김 | 직관적             | 스택 오버플로우 위험 없음              |
| 재귀   | 짧고 간결     | 수학적 표현과 유사 | 깊은 재귀 호출 시 스택 오버플로우 가능 |

- **재귀 방식**은 코드가 더 간결하지만, 입력값이 매우 큰 경우(예: gcdRecursive(10⁹, 10⁸)) **스택오버플로우** 위험이 있을 수 있다.
- **반복문 방식**은 스택을 사용하지 않으므로 **안정적**이다.

## 🔥 정리

- 유클리드 호제법을 사용하면 O(log N) 시간 복잡도로 최대공약수를 구할 수 있다.
- 반복문과 재귀 방식이 있으며, 실행 속도는 비슷하지만 재귀 호출이 깊어지면 스택 오버플로우 위험이 있다.
