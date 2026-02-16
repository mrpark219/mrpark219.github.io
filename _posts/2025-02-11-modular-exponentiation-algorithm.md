---
title: ⚙️ 모듈러 거듭제곱 알고리즘
date: 2025-02-11 22:12 +0900
description: 모듈러 거듭제곱 알고리즘의 원리, 계산 예시, Kotlin 구현 코드를 쉽게 정리.
categories: [알고리즘]
tags: [알고리즘, 수학]
image: /assets/blog-images/posts/2025-02-11-modular-exponentiation-algorithm/title.png
math: true
---

> **모듈러 거듭제곱(Modular Exponentiation)**: 거듭제곱을 계산하면서 특정 수로 나눈 나머지를 구하는 알고리즘이다. 큰 수의 연산을 줄여 메모리 친화적이고 효율적인 방식으로 계산할 수 있다.

## 1. 모듈러 연산의 기본 성질

모듈러 연산을 활용하면 큰 수의 연산을 줄일 수 있다.
기본적인 모듈러 연산 성질은 다음과 같다.

1. 덧셈의 모듈러 연산: $(a + b) \bmod m = [(a \bmod m) + (b \bmod m)] \bmod m$
2. 뺄셈의 모듈러 연산: $(a - b) \bmod m = [(a \bmod m) - (b \bmod m) + m] \bmod m$
3. 곱셈의 모듈러 연산: $(a \times b) \bmod m = [(a \bmod m) \times (b \bmod m)] \bmod m$
4. 거듭제곱의 모듈러 연산: $a^n \bmod m = [(a \bmod m)^n] \bmod m$  
   지수가 커질 경우 직접 계산하면 시간 초과가 발생할 수 있다.  
   이를 해결하기 위해 **모듈러 거듭제곱 알고리즘**을 사용한다.

## 2. 모듈러 거듭제곱 알고리즘

거듭제곱을 계산할 때, 매 연산마다 모듈러 연산을 적용하면 큰 수의 연산을 방지할 수 있다. 지수를 절반으로 줄이는 빠른 거듭제곱 방식을 활용하여 연산량을 줄인다.

1. 지수가 **짝수**일 때:
   $$a^n \bmod m = (a^{n/2} \bmod m)^2 \bmod m$$
2. 지수가 **홀수**일 때:
   $$a^n \bmod m = (a \times (a^{n/2} \bmod m)^2) \bmod m$$

이 방식을 사용하면 시간 복잡도를 **$O(\log N)$** 으로 줄일 수 있다.

## 3. 예제 $3^{13} \bmod 7$ 계산하기

### 일반적인 방법

$$
\begin{gather}
3^{13} = 1594323 \\
1594323 \bmod 7 = 3
\end{gather}
$$

### 모듈러 거듭제곱을 이용한 방법

1. 지수가 홀수: $3^{13} \bmod 7 = (3 \times 3^{12} \bmod 7) \bmod 7$
2. 지수가 짝수: $3^{12} \bmod 7 = (3^6 \bmod 7)^2 \bmod 7$
3. 지수가 짝수: $3^6 \bmod 7 = (3^3 \bmod 7)^2 \bmod 7$
4. 지수가 홀수: $3^3 \bmod 7 = (3 \times 3^2 \bmod 7) \bmod 7$
5. 지수가 짝수: $3^2 \bmod 7 = 9 \bmod 7 = 2$

### 모듈러 거듭제곱 계산 과정

- $3^2 \bmod 7 = 2$
- $3^3 \bmod 7 = (3 \times 2) \bmod 7 = 6$
- $3^6 \bmod 7 = (6^2) \bmod 7 = 36 \bmod 7 = 1$
- $3^{12} \bmod 7 = (1^2) \bmod 7 = 1$
- $3^{13} \bmod 7 = (3 \times 1) \bmod 7 = 3$

## 4. 예제 코드 (재귀 방식)

```kotlin
fun modPow(base: Long, exp: Long, mod: Long): Long {
    if(exp == 0L) return 1  // 지수가 0이면 1 반환 (기저 조건)

    val half = modPow(base, exp / 2, mod)  // 지수를 절반으로 줄여서 재귀 호출
    val result = (half * half) % mod  // 모듈러 연산 적용

    return if(exp % 2 == 0L) result else (result * (base % mod)) % mod  // 지수가 홀수면 base 추가 곱셈
}
```

## 5. 예제 코드 (반복문 방식)

```kotlin
fun modPow(base: Long, exp: Long, mod: Long): Long {
    var result = 1L
    var b = base % mod  // 처음부터 mod 연산 적용
    var e = exp

    while(e > 0) {
        if(e and 1L == 1L) {  // 지수가 홀수이면 결과에 base 곱하기
            result = (result * b) % mod
        }
        b = (b * b) % mod  // 밑을 제곱
        e = e shr 1  // 지수를 반으로 줄이기(e /= 2)
    }

    return result
}
```

## 🔥 정리

- 일반적인 거듭제곱 연산은 $O(N)$ 이지만, 모듈러 거듭제곱을 사용하면 $O(\log N)$ 으로 최적화할 수 있다.
- 매 연산마다 모듈러 연산을 적용하여 큰 수의 연산을 방지할 수 있다.
- 알고리즘 문제에서 "어떤 수를 $10^9+7$로 나눈 나머지를 구하라" 는 유형에서 많이 사용된다.
- 연산 횟수를 줄이므로 메모리 및 실행 속도 측면에서 유리하다.
