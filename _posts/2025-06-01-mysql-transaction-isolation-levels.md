---
title: MySQL 트랜잭션 격리 수준(Isolation Level)
date: 2025-06-04 00:30 +0900
last_modified_at: 2026-08-25 00:00:00 +0900
description: MySQL 트랜잭션 격리 수준별 특징과 Dirty Read, Non-Repeatable Read, Phantom Read를 SQL 예제로 정리.
categories: [백엔드]
tags: [백엔드, 데이터베이스, 트랜잭션]
image: /assets/blog-images/posts/2025-06-01-mysql-transaction-isolation-levels/2025-06-04-00-34-50.png
mermaid: true
---

## 1. 트랜잭션의 격리 수준 (Transaction Isolation Level)

- 여러 트랜잭션이 동시에 처리될 때, 한 트랜잭션이 다른 트랜잭션의 데이터 변경이나 조회 결과를 볼 수 있도록 허용할지 여부를 결정하는 기준이다.
- 격리 수준은 **동시성 성능과 데이터 일관성 보장 간의 trade-off**를 조절하는 역할을 한다.
- 격리 수준은 아래와 같이 **낮은 순서(= 제약이 적은 순서)**로 나열된다:
  - `READ UNCOMMITTED`
  - `READ COMMITTED`
  - `REPEATABLE READ`
  - `SERIALIZABLE`

## 2. 격리 수준에서 발생할 수 있는 이상 현상 (Anomaly)

격리 수준이 낮을수록 아래 세 가지 이상 현상이 발생할 가능성이 커진다.

- **Dirty Read (더티 리드)**
  - 다른 트랜잭션이 아직 커밋하지 않은 데이터를 읽는 현상이다.
  - 만약 그 트랜잭션이 이후 롤백되면, 애초에 존재한 적 없는 데이터를 읽은 셈이 되어 문제가 된다.

- **Non-Repeatable Read (반복 불가능한 읽기)**
  - 하나의 트랜잭션 안에서 같은 row를 두 번 조회했는데, 그 사이 다른 트랜잭션이 해당 row를 `UPDATE`하고 커밋해서 두 조회 결과의 값이 달라지는 현상이다.
  - 조회 대상 row 자체는 동일하지만 **값**이 바뀐다는 점이 특징이다.

- **Phantom Read (팬텀 리드)**
  - 하나의 트랜잭션 안에서 동일한 조건으로 범위를 조회했는데, 그 사이 다른 트랜잭션이 조건에 맞는 row를 `INSERT`(또는 `DELETE`)하고 커밋해서 조회되는 row의 **집합**(개수)이 달라지는 현상이다.
  - Non-Repeatable Read가 이미 존재하던 row의 값 변화라면, Phantom Read는 없던 row가 나타나거나(또는 있던 row가 사라져) 결과 집합 자체가 바뀌는 것이 차이점이다.

## 3. READ UNCOMMITTED

- 가장 낮은 수준의 격리 단계이다.
- 다른 트랜잭션에서 아직 커밋하지 않은 **미완료 데이터까지 읽는 것이 가능하다**.
- 따라서 **더러운 읽기(dirty read)** 가 발생할 수 있다.
- 트랜잭션 간 간섭이 거의 없기 때문에 **성능은 높지만, 데이터 일관성은 매우 낮다**.
- 일반적으로 실무에서는 거의 사용하지 않는다.

```mermaid
sequenceDiagram
    participant A as 트랜잭션 A
    participant B as 트랜잭션 B

    A->>DB: UPDATE accounts SET balance = balance - 100 WHERE id = 1;
    B->>DB: SELECT balance FROM accounts WHERE id = 1;
    B-->>User: 커밋 전 변경된 값 조회 (Dirty Read)
    A->>DB: ROLLBACK;
```

```sql
-- 트랜잭션 A
SET SESSION TRANSACTION ISOLATION LEVEL READ UNCOMMITTED;
START TRANSACTION;
UPDATE accounts SET balance = balance - 100 WHERE id = 1;

-- 트랜잭션 B
SET SESSION TRANSACTION ISOLATION LEVEL READ UNCOMMITTED;
START TRANSACTION;
SELECT balance FROM accounts WHERE id = 1;

-- 트랜잭션 A
ROLLBACK;
```

## 4. READ COMMITTED

- 대부분의 상용 DBMS에서 기본값으로 설정되어 있는 격리 수준이다.
- **트랜잭션이 커밋한 데이터만 읽을 수 있도록 허용한다**.
- **더러운 읽기(dirty read)** 는 방지할 수 있지만, **반복 불가능한 읽기**와 **팬텀 리드**는 발생할 수 있다.
- 트랜잭션 중 같은 SELECT를 여러 번 수행해도 결과가 바뀔 수 있기 때문에 주의가 필요하다.
- Oracle의 기본 격리 수준이 `READ COMMITTED`이다.

```mermaid
sequenceDiagram
    participant A as 트랜잭션 A
    participant B as 트랜잭션 B

    A->>DB: SELECT salary FROM employee WHERE id = 1 (결과: 3000)
    B->>DB: UPDATE employee SET salary = 4000 WHERE id = 1
    B->>DB: COMMIT
    A->>DB: SELECT salary FROM employee WHERE id = 1 (결과: 4000)
```

```sql
-- 트랜잭션 A
SET SESSION TRANSACTION ISOLATION LEVEL READ COMMITTED;
START TRANSACTION;
SELECT salary FROM employee WHERE id = 1;

-- 트랜잭션 B
SET SESSION TRANSACTION ISOLATION LEVEL READ COMMITTED;
START TRANSACTION;
UPDATE employee SET salary = 4000 WHERE id = 1;
COMMIT;

-- 트랜잭션 A
SELECT salary FROM employee WHERE id = 1;
```

## 5. REPEATABLE READ

- 동일 트랜잭션 내에서 **같은 쿼리를 여러 번 실행해도 항상 동일한 결과를 보장한다**.
- **반복 불가능한 읽기(non-repeatable read)** 와 **더러운 읽기(dirty read)** 를 방지할 수 있다.
- 하지만 **팬텀 리드(phantom read)** 는 방지하지 못한다.
- MySQL의 InnoDB 엔진에서는 기본 격리 수준이 `REPEATABLE READ`이며, 일반적으로는 팬텀 리드까지 방지하도록 구현되어 있다.
- 다만 트랜잭션 안에서 **처음으로** `SELECT ... FOR UPDATE`(락킹 리드)를 실행하면, 그 시점부터는 자신의 MVCC 스냅샷이 아니라 최신 커밋 데이터를 읽기 때문에 팬텀 리드가 발생할 수 있다.
  - 반대로 처음부터 `FOR UPDATE`로 조회했다면 해당 범위에 갭 락이 걸려 다른 트랜잭션의 `INSERT`가 블로킹되므로, 같은 `FOR UPDATE` 조회를 반복해도 그 사이에는 팬텀 리드가 발생하지 않는다.

```mermaid
sequenceDiagram
    participant A as 트랜잭션 A
    participant B as 트랜잭션 B

    A->>DB: SELECT * FROM orders WHERE amount > 100 (락 없는 일반 조회)
    B->>DB: INSERT INTO orders(amount) VALUES (200);
    B->>DB: COMMIT;
    A->>DB: SELECT * FROM orders WHERE amount > 100 FOR UPDATE (새로 삽입된 row 포함 - Phantom Read)
```

```sql
-- 트랜잭션 A
SET SESSION TRANSACTION ISOLATION LEVEL REPEATABLE READ;
START TRANSACTION;
SELECT * FROM orders WHERE amount > 100;

-- 트랜잭션 B
SET SESSION TRANSACTION ISOLATION LEVEL REPEATABLE READ;
START TRANSACTION;
INSERT INTO orders(amount) VALUES (200);
COMMIT;

-- 트랜잭션 A (첫 락킹 리드 - 최신 커밋 데이터를 읽어 새 row가 보인다)
SELECT * FROM orders WHERE amount > 100 FOR UPDATE;
```

## 6. SERIALIZABLE

- 가장 높은 수준의 격리 단계이며, **트랜잭션을 마치 순차적으로 처리하는 것처럼 보이게 만든다**.
- 모든 트랜잭션이 **동시에 동일한 데이터를 조회하거나 수정하는 것을 허용하지 않는다**.
- **팬텀 리드(phantom read)**, **반복 불가능한 읽기(non-repeatable read)**, **더러운 읽기(dirty read)** 등 모든 문제가 발생하지 않도록 방지한다.
- 완벽한 일관성을 보장하지만, 그만큼 **동시 처리 성능은 가장 낮다**.
- 주로 데이터 정확성이 가장 중요한 금융/회계 시스템 등에서 사용한다.

## 7. 격리 수준별 허용되는 현상 정리

| 격리 수준        | Dirty Read | Non-Repeatable Read | Phantom Read |
| ---------------- | ---------- | ------------------- | ------------ |
| READ UNCOMMITTED | ✅         | ✅                  | ✅           |
| READ COMMITTED   | ❌         | ✅                  | ✅           |
| REPEATABLE READ  | ❌         | ❌                  | ✅           |
| SERIALIZABLE     | ❌         | ❌                  | ❌           |
