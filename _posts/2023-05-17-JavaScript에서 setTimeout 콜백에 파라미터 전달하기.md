---
title: JavaScript에서 setTimeout 콜백에 파라미터 전달하기
date: 2023-05-17 20:00:00 +0900
categories:
  - JavaScript
tags:
  - setTimeout
---

## setTimeout 함수 개요

JavaScript에서 `setTimeout` 함수는 특정 시간이 지난 후에 함수를 실행하는 데 사용됩니다. 이 함수는 두 개의 파라미터를 받습니다: 첫 번째는 실행할 함수이고, 두 번째는 시간을 밀리초 단위로 나타냅니다. 그런데 이 함수를 사용하면서 콜백 함수에 추가적인 파라미터를 전달하고 싶을 때가 있습니다. 이 문제를 해결하는 몇 가지 방법이 있습니다.

## 방법 1: 익명 함수 사용하기

익명 함수(Anonymous Function)는 이름이 없는 함수입니다. 이를 사용하여 `setTimeout`에 콜백 함수와 함께 파라미터를 전달할 수 있습니다.

```javascript
setTimeout(function() {
    myFunction(param1, param2);
}, 2000);
```

여기서 `myFunction`은 실행할 함수이고, `param1`과 `param2`는 그 함수에 전달할 파라미터입니다.

## 방법 2: bind 메서드 활용하기

JavaScript의 `bind` 메서드를 사용하면 함수에 파라미터를 미리 설정할 수 있습니다. 이 메서드는 새로운 함수를 반환합니다.

```javascript
setTimeout(myFunction.bind(null, param1, param2), 2000);
```

`bind`의 첫 번째 파라미터는 함수의 `this` 값입니다. 여기서는 `null`을 사용했습니다.

## 방법 3: 화살표 함수 활용하기

ES6에서 도입된 화살표 함수(Arrow Function)도 `setTimeout`에서 파라미터를 전달하는 데 사용할 수 있습니다.

```javascript
setTimeout(() => myFunction(param1, param2), 2000);
```

화살표 함수는 코드를 더 간결하게 만들어 줍니다.

## 결론

JavaScript에서 `setTimeout` 함수를 사용하여 특정 시간 후에 함수를 실행할 때 추가적인 파라미터를 전달하는 방법은 여러 가지입니다. 익명 함수, `bind` 메서드, 화살표 함수 등을 활용하여 이 문제를 해결할 수 있습니다. 각 방법은 상황과 필요에 따라 선택하면 됩니다.