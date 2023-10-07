---
title: TypeScript에서 꼬리 재귀 최적화 구현하기
date: 2023-08-15 20:00:00 +0900
categories:
  - JavaScript
tags:
  - TypeScript
---

## 꼬리 재귀 최적화란?

꼬리 재귀(Tail Recursion) 최적화는 프로그래밍 언어에서 특히 함수 호출을 더 효율적으로 만들기 위한 방법입니다. 꼬리 재귀는 함수의 마지막 연산이 자기 자신을 호출하는 형태를 가리킵니다. 최적화는 이러한 호출을 일반적인 반복문처럼 실행하여 메모리와 시간을 절약하는 과정입니다.

## TypeScript에서는 어떻게 적용하나?

TypeScript는 자바스크립트를 기반으로 하며, 자바스크립트 엔진이 꼬리 재귀 최적화를 지원하지 않기 때문에 TypeScript 자체에서 이를 지원하지 않습니다. 하지만 몇 가지 방법이 있습니다.

### 방법 1: 명시적인 루프 사용하기

가장 간단하고 직관적인 방법은 재귀 함수 대신 명시적인 루프를 사용하는 것입니다. 이렇게 하면 함수 호출에 따른 오버헤드가 없어져 성능이 향상됩니다.

```typescript
function factorial(n: number): number {
  let result = 1;
  for (let i = 1; i <= n; ++i) {
    result *= i;
  }
  return result;
}
```

### 방법 2: Trampoline 함수 사용하기

Trampoline 함수는 꼬리 재귀를 반복문으로 변환해주는 함수입니다. 이 방법은 함수 호출의 스택 오버플로우를 방지해줍니다.

```typescript
function trampoline<T>(fn: (...args: any[]) => any): (...args: any[]) => T {
  return (...args: any[]): T => {
    let result = fn(...args);
    while (typeof result === 'function') {
      result = result();
    }
    return result;
  };
}
```

### 오류 이름

StackOverflowError

## 결론

TypeScript에서 꼬리 재귀 최적화를 완벽하게 구현할 수는 없지만, 명시적인 루프 사용이나 Trampoline 함수를 활용하면 성능을 향상시킬 수 있습니다. 이러한 방법들은 메모리 사용량을 줄이고 실행 속도를 빠르게 해주므로, 복잡한 연산을 수행할 때 유용합니다.