---
title: JavaScript에서 undefined와 null 변수 확인하는 방법
date: 2023-06-07 20:00:00 +0900
categories:
  - JavaScript
tags:
  - 자바스크립트널
---

## 소개
JavaScript는 웹 개발에서 가장 널리 사용되는 프로그래밍 언어 중 하나입니다. 이 언어에서는 변수가 정의되지 않았거나 null인지 확인하는 것이 매우 중요합니다. 이 글에서는 이러한 변수를 어떻게 확인하는지에 대해 상세하게 알아보겠습니다.

## `undefined`와 `null`이 무엇인가요?

`undefined`는 변수가 선언되었지만 아직 값이 할당되지 않았을 때의 상태입니다. 반면 `null`은 변수에 의도적으로 값이 없음을 나타내기 위해 사용됩니다. 

## `undefined`와 `null` 확인하기: 기본적인 방법

JavaScript에서 변수가 `undefined` 또는 `null`인지 확인하는 가장 간단한 방법은 `===` 연산자를 사용하는 것입니다. 

```javascript
if (variable === undefined) {
  // 코드 실행
}

if (variable === null) {
  // 코드 실행
}
```

## `typeof` 연산자 사용하기

`typeof` 연산자는 변수의 데이터 타입을 문자열로 반환합니다. `undefined`를 확인할 때 유용하게 사용될 수 있습니다.

```javascript
if (typeof variable === "undefined") {
  // 코드 실행
}
```

## `null`과 `undefined`를 동시에 확인하기

JavaScript에서는 `null`과 `undefined`가 서로 동등하다고 판단되기 때문에 `==` 연산자를 사용하여 둘을 동시에 확인할 수 있습니다.

```javascript
if (variable == null) {
  // 코드 실행
}
```

## 주의사항

- `undefined`와 `null`은 자료형이 다르므로 `===`로 비교할 때는 동일하지 않습니다.
- 명시적으로 `null`을 할당하지 않은 변수는 `undefined` 상태입니다.

## 정리

변수가 `undefined` 또는 `null`인지 확인하는 것은 자주 발생하는 작업입니다. 이를 위해 `===` 연산자나 `typeof` 연산자를 적절히 사용하면 됩니다. 또한, `==` 연산자를 사용하면 `null`과 `undefined`를 동시에 확인할 수 있습니다. 이 방법들을 이해하고 활용하면 JavaScript에서 더 효과적인 코드를 작성할 수 있습니다.