---
title: 자바스크립트에서 Missing Parameter 오류 해결 방법
date: 2023-07-03 20:00:00 +0900
categories:
  - JavaScript
tags:
  - 자바스크립트오류
---

## 오류 원인 및 발생 상황

자바스크립트에서 `Missing Parameter`라는 오류는 함수를 호출할 때 필요한 매개변수를 누락했을 때 발생합니다. 매개변수란 함수에 정보를 전달하는 역할을 하는 변수입니다. 예를 들어, `function add(a, b)`라는 함수가 있다면 이 함수는 `a`와 `b` 두 개의 매개변수를 필요로 합니다.

## 문제 해결을 위한 첫 번째 방법: 매개변수 확인

가장 먼저 해야 할 일은 코드에서 함수를 호출하는 부분을 찾아서 필요한 매개변수가 모두 들어가 있는지 확인하는 것입니다. 이때, 함수 선언부와 함수 호출부의 매개변수가 일치해야 합니다.

```javascript
function add(a, b) {
  return a + b;
}

// 올바른 함수 호출
const result = add(1, 2);

// 오류 발생: Missing Parameter
const wrongResult = add(1);
```

## 문제 해결을 위한 두 번째 방법: 기본값 설정

매개변수에 기본값을 설정해두면, 함수를 호출할 때 해당 매개변수를 누락해도 오류가 발생하지 않습니다. 자바스크립트에서는 이를 위해 ES6부터 기본 매개변수 문법을 제공합니다.

```javascript
function add(a, b = 0) {
  return a + b;
}

// 오류 없이 실행됨
const result = add(1);
```

## 문제 해결을 위한 세 번째 방법: 조건문 사용

매개변수가 누락될 가능성이 있다면, 함수 내부에서 조건문을 사용해 이를 검사할 수 있습니다.

```javascript
function add(a, b) {
  if (b === undefined) {
    b = 0;
  }
  return a + b;
}

// 오류 없이 실행됨
const result = add(1);
```

## 정리

`Missing Parameter` 오류는 주로 함수의 매개변수가 누락되었을 때 발생합니다. 이 오류를 해결하기 위한 세 가지 방법은 매개변수 확인, 기본값 설정, 조건문 사용입니다. 이 세 가지 방법을 잘 활용하면 오류를 효과적으로 해결할 수 있습니다.