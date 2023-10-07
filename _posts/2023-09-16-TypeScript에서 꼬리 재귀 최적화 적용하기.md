---
title: TypeScript에서 꼬리 재귀 최적화 적용하기
date: 2023-09-16 20:00:00 +0900
categories:
  - JavaScript
tags:
  - TypeScript
---

## 문제 상황: Tail Recursion Optimization이 작동하지 않는 이유

꼬리 재귀(Tail Recursion)는 함수가 자신을 호출할 때 마지막 연산으로 자기 자신을 호출하는 것을 의미합니다. 이러한 꼬리 재귀는 스택 오버플로(Stack Overflow)의 위험을 줄이기 위해 일반적으로 최적화됩니다. 그러나 TypeScript에서는 이러한 최적화가 자동으로 이루어지지 않습니다. 이로 인해 'RangeError: Maximum call stack size exceeded' 같은 오류가 발생할 수 있습니다.

## 해결 방법: TypeScript 컴파일러 옵션 활용

TypeScript에서 꼬리 재귀 최적화를 적용하려면 `tsconfig.json` 파일에서 `"downlevelIteration": true` 옵션을 설정해야 합니다. 이 옵션은 TypeScript가 ECMAScript 2015 이상의 버전으로 컴파일될 때, 꼬리 재귀 최적화를 가능하게 합니다. 그런 다음 아래와 같이 코드를 작성하면 됩니다.

```typescript
function factorial(n: number, acc: number = 1): number {
  if (n <= 1) return acc;
  return factorial(n - 1, n * acc);
}
```

## 추가 팁: 코드 리팩토링을 통한 최적화

코드 리팩토링(Refactoring)은 코드의 구조를 개선하면서 기능은 그대로 유지하는 것입니다. 꼬리 재귀 최적화를 적용하기 위해 코드를 리팩토링할 수 있습니다. 예를 들어, 재귀 함수를 다음과 같이 수정하여 최적화할 수 있습니다.

```typescript
function optimizedFactorial(n: number): number {
  function helper(n: number, acc: number): number {
    if (n <= 1) return acc;
    return helper(n - 1, n * acc);
  }
  return helper(n, 1);
}
```

이렇게 하면 TypeScript에서도 꼬리 재귀 최적화를 적용할 수 있습니다. 이 방법을 통해 스택 오버플로의 위험을 크게 줄일 수 있으며, 프로그램의 성능도 향상시킬 수 있습니다.