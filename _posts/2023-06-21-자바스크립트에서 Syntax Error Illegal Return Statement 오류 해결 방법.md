---
title: 자바스크립트에서 Syntax Error Illegal Return Statement 오류 해결 방법
date: 2023-06-21 20:00:00 +0900
categories:
  - JavaScript
tags:
  - 자바스크립트오류
---

## 오류의 발생 배경

'`Syntax Error: Illegal Return Statement`'는 자바스크립트에서 코드를 작성하다 발생할 수 있는 문법 오류입니다. 이 오류는 주로 `return` 문이 적절하지 않은 위치에 쓰였을 때 나타납니다. 이를 이해하기 위해 자바스크립트의 `return` 문에 대해 간단히 살펴보면, `return` 문은 함수 내부에서만 사용되어야 합니다. 만약 함수 밖이나 조건문, 반복문 같은 블록 외부에서 사용되면 이 오류가 발생합니다.

## 해결 방법 1: 함수 내부로 이동

가장 쉬운 해결 방법은 `return` 문을 함수 내부로 옮기는 것입니다. 예를 들어 아래와 같은 코드가 있다면,

```javascript
if (true) {
  return false; // 문법 오류 발생!
}
```

이를 다음과 같이 수정할 수 있습니다.

```javascript
function checkCondition() {
  if (true) {
    return false; // 문제 없음
  }
}
```

## 해결 방법 2: 적절한 블록 구조 활용

`return` 문이 if 문 또는 for 문과 같은 블록 내부에 있을 때, 그 블록이 함수 내부에 있는지 확인해야 합니다. 예를 들어, 다음과 같은 코드는 오류를 발생시킵니다.

```javascript
function myFunction() {
  for (let i = 0; i < 5; i++) {
    if (i === 3) {
      return true; // 문제 없음
    }
  }
}
```

## 해결 방법 3: return 문 없애기

모든 함수가 반드시 `return` 문을 필요로 하는 것은 아닙니다. 필요 없다면 `return` 문 자체를 제거할 수 있습니다. 그러면 함수는 자동으로 `undefined` 값을 반환합니다.

## 정리

'`Syntax Error: Illegal Return Statement`' 오류는 대체로 `return` 문의 잘못된 위치 때문에 발생합니다. 이 오류를 해결하기 위해 `return` 문이 올바른 위치, 즉 함수 내부에 있는지 확인하고, 필요하다면 코드의 구조를 변경해야 합니다. 이렇게 하면 문제를 쉽게 해결할 수 있습니다.