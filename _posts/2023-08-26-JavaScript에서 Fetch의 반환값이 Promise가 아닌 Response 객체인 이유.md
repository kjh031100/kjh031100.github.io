---
title: JavaScript에서 Fetch의 반환값이 Promise가 아닌 Response 객체인 이유
date: 2023-08-26 20:00:00 +0900
categories:
  - JavaScript
tags:
  - Fetch반환값
  - promise
  - Response
  - 자바스크립트
---

## 개요

JavaScript에서 `fetch` 함수를 사용할 때 종종 이해하기 어려운 부분 중 하나는 왜 이 함수가 Promise 객체 대신 Response 객체를 반환하는지입니다. 이 문제를 명확하게 이해하기 위해 `fetch`의 작동 원리와 Promise, Response 객체의 역할을 자세히 살펴보겠습니다.

## Fetch 함수와 Promise

`fetch` 함수는 웹에서 데이터를 가져오는 역할을 합니다. 이 함수를 호출하면, 실제로 반환되는 것은 `Promise` 객체입니다. Promise는 비동기 작업이 완료될 때까지 기다리고, 그 결과를 나중에 처리할 수 있게 하는 객체입니다. 즉, `fetch`가 반환하는 Promise는 HTTP 요청이 완료되기를 기다립니다.

## Response 객체의 등장

Promise가 완료되면 `.then()` 메서드를 사용하여 결과를 처리할 수 있습니다. 이때 결과는 `Response` 객체입니다. Response 객체는 HTTP 응답과 관련된 여러 정보와 메서드를 포함하고 있습니다. 예를 들어, 응답 헤더, 상태 코드, 본문 등이 있습니다.

## 오해의 원인: Response 객체와 Promise

많은 사람들이 `fetch`가 직접 Response 객체를 반환한다고 오해하는 이유는 `.then()`을 통해 Response 객체에 접근하기 때문입니다. 사실, `fetch`는 Promise를 반환하고, 이 Promise가 완료되면 Response 객체가 반환됩니다.

## 예제: Fetch와 Response 객체

```javascript
fetch('https://api.example.com/data')
  .then(response => response.json())
  .then(data => console.log(data))
  .catch(error => console.log('Error:', error));
```

이 예제에서 `fetch` 함수는 Promise를 반환합니다. 이 Promise가 완료되면, `.then()` 메서드를 통해 Response 객체에 접근할 수 있습니다. `response.json()`은 Response 객체의 본문을 JSON 형식으로 변환합니다.

## 정리

`fetch` 함수는 Promise 객체를 반환하며, 이 Promise가 완료되면 `Response` 객체로 결과를 제공합니다. 이로 인해 `fetch`가 직접 Response 객체를 반환하는 것처럼 보이지만, 실제로는 Promise를 통해 Response 객체에 접근하는 것입니다. 이 점을 이해하면, `fetch`의 작동 원리를 보다 명확하게 파악할 수 있습니다.