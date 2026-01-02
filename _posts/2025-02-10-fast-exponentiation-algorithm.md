---
title: ⚙️ 빠른 거듭제곱 알고리즘
date: 2025-02-10 22:27 +0900
categories: [알고리즘]
tags: [알고리즘, 개념]
image: /assets/blog-images/posts/2025-02-10-fast-exponentiation-algorithm/title.png
math: true
---

> **빠른 거듭제곱(Fast Exponentiation)**: 거듭제곱을 빠르게 계산하는 알고리즘이다. 일반적으로 $a^n$를 구할 때 $O(N)$의 시간이 걸리지만, 빠른 거듭제곱을 사용하면 **$O(log N)$** 로 줄일 수 있다.

## 1. 빠른 거듭제곱 기본 연산

거듭제곱의 성질을 이용해서 지수를 반 씩 줄여나가는 방식이다.

1. 지수가 **짝수**일 때:
   $$a^n = (a^{n/2})^2$$

2. 지수가 **홀수**일 때:
   $$a^n = a \times (a^{n/2})^2$$

위 방식을 통해 한 번의 연산으로 지수를 절반씩 줄일 수 있어 계산량을 대폭 줄일 수 있다.

## 2. 예제 $5^{12}$ 계산하기

### 일반적인 방법

$$5^{12} = 5 \times 5 \times 5 \times 5 \times 5 \times 5 \times 5 \times 5 \times 5 \times 5 \times 5 \times 5$$

이렇게 12번 곱해야 하지만, 빠른 거듭제곱을 사용하면 지수를 절반씩 줄일 수 있다.

### 빠른 거듭제곱

1.  지수가 짝수: $5^{12} = (5^6)^2$
2.  지수가 짝수: $5^6 = (5^3)^2$
3.  지수가 홀수: $5^3 = 5 \times (5^1)^2$
4.  기저 조건 도달: $5^1 = 5$

### 빠른 거듭제곱 계산 과정

- $5^1 = 5$
- $5^3 = 5 \times (5^1)^2 = 5 \times 25 = 125$
- $5^6 = (5^3)^2 = 125^2 = 15625$
- $5^{12} = (5^6)^2 = 15625^2 = 244140625$

## 3. 예시 코드(재귀 방식)

```kotlin
fun fastPow(base: Long, exp: Long): Long {
    if(exp == 0L) return 1  // 지수가 0이면 1 반환 (기저 조건)

    val half = fastPow(base, exp / 2)  // 지수를 절반으로 줄여서 재귀 호출

    // 지수가 짝수이면 half^2, 홀수이면 half^2 * base 반환
    return if(exp % 2 == 0L) half * half else half * half * base
}
```

## 4. 예시 코드(반복문 방식)

반복문을 사용해서 지수가 0이 될 때까지 나누면서 계산하는 방식

```kotlin
fun fastPow(base: Long, exp: Long): Long {
    var result = 1L
    var b = base
    var e = exp

    while(e > 0) {
        if(e and 1L == 1L) {
            result *= b  // 지수가 홀수면 결과에 곱하기
        }
        b *= b  // 밑을 제곱
        e = e shr 1  // 지수를 반으로 줄이기(e /= 2)
    }

    return result
}
```

## 🔥 정리

- 일반적인 거듭제곱 연산은 $O(N)$ 시간이 걸리지만, 빠른 거듭제곱은 $O(\log N)$ 으로 줄일 수 있다.
- 빠른 거듭제곱은 한 번 연산할 때마다 지수가 반으로 줄어든다. 따라서 지수가 $N$ 일 때 필요한 연산 횟수는 약 $log_2 N$ 번이다.
