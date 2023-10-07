---
title: JavaScript에서 forEach is not a function 오류 해결하기
date: 2023-07-01 20:00:00 +0900
categories:
  - JavaScript
tags:
  - 자바스크립트오류
---

## 오류 발생 원인

JavaScript에서 배열에 대해 `forEach` 함수를 사용할 때 종종 발생하는 오류 중 하나는 "forEach is not a function"입니다. 이 오류는 주로 변수가 실제 배열이 아니라 배열과 유사한 객체일 때 발생합니다. JavaScript의 배열과 배열과 유사한 객체는 다르기 때문에, 실제 배열이 아닌 것에 `forEach`를 적용하려고 하면 이 오류가 발생합니다.

## 해결 방법 1: Array.from() 사용하기

JavaScript에서 `Array.from()` 메서드를 사용하면 배열과 유사한 객체를 실제 배열로 변환할 수 있습니다. 예를 들어, `arguments` 객체나 `NodeList` 객체는 배열과 유사한 객체입니다. 이런 객체에 `forEach`를 적용하려면 먼저 `Array.from()`을 사용하여 실제 배열로 변환해야 합니다.

```javascript
let arrayLikeObject = {0: 'a', 1: 'b', length: 2};
let trueArray = Array.from(arrayLikeObject);
trueArray.forEach(element => console.log(element));
```

## 해결 방법 2: 스프레드 연산자 사용하기

스프레드 연산자(`...`)도 배열과 유사한 객체를 실제 배열로 변환하는데 사용할 수 있습니다. 스프레드 연산자는 배열 또는 배열과 유사한 객체의 요소를 개별적으로 분리하여 새 배열을 생성합니다.

```javascript
let arrayLikeObject = {0: 'a', 1: 'b', length: 2};
let trueArray = [...arrayLikeObject];
trueArray.forEach(element => console.log(element));
```

## 해결 방법 3: for 루프 사용하기

`forEach`가 작동하지 않을 경우, 기본적인 `for` 루프를 사용하는 것도 하나의 방법입니다. `for` 루프는 모든 종류의 객체와 배열에서 작동하므로, 이 오류를 피할 수 있습니다.

```javascript
let arrayLikeObject = {0: 'a', 1: 'b', length: 2};
for (let i = 0; i < arrayLikeObject.length; i++) {
    console.log(arrayLikeObject[i]);
}
```

## 요약

"forEach is not a function" 오류는 주로 배열과 유사한 객체에 `forEach`를 적용할 때 발생합니다. 이 오류를 해결하는 방법은 여러 가지가 있으며, 그 중 하나를 선택하여 적용할 수 있습니다. 이러한 방법을 알고 있으면 이 오류를 빠르게 해결할 수 있습니다.