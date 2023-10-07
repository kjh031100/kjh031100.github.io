---
title: Fetch 함수가 Response 객체를 반환하는 이유
date: 2023-09-27 20:00:00 +0900
categories:
  - JavaScript
tags:
  - Fetch함수
  - Response객체
---

## 서론: Fetch와 Promise

Fetch API는 웹에서 데이터를 가져오는 데 사용되는 자바스크립트의 내장 함수입니다. `fetch()` 함수가 호출되면, 이 함수는 `Promise` 객체를 반환합니다. `Promise`는 미래에 완료될 작업의 결과를 나타내며, 이 결과는 성공 또는 실패일 수 있습니다. 그러나 많은 개발자가 `fetch` 함수를 실행한 후에 반환된 객체가 `Promise`가 아닌 `Response` 객체임을 궁금해합니다.

## Response 객체와 Promise의 관계

Fetch 함수가 반환하는 Promise는 실제로 `Response` 객체를 가리킵니다. 즉, 이 Promise가 성공적으로 완료될 때 (`then` 또는 `async/await`를 사용하여 처리), 그 결과는 `Response` 객체가 됩니다. 이 `Response` 객체는 서버로부터 받은 응답을 나타내며, 이 객체를 통해 다양한 작업을 수행할 수 있습니다. 예를 들어 `Response.json()` 메서드를 호출하면, 이 응답을 JSON 형식으로 파싱할 수 있습니다.

## 왜 Response 객체가 필요한가?

`Response` 객체는 HTTP 응답에 대한 상세한 정보를 포함합니다. 이에는 상태 코드(Status Code), 헤더(Headers), 본문(Body) 등이 포함됩니다. 그래서 개발자는 `Response` 객체를 사용하여 더 다양한 작업을 수행할 수 있습니다. 예를 들어, 서버 응답이 404 상태 코드를 반환한 경우 해당 리소스가 없음을 알 수 있고, 이에 따른 조치를 취할 수 있습니다.

## 코드 예제: fetch 사용법

아래는 간단한 `fetch` 함수의 사용 예입니다.

```javascript
fetch('https://api.example.com/data')
  .then(response => response.json())
  .then(data => console.log(data))
  .catch(error => console.log('Error:', error));
```

이 예에서 `fetch` 함수는 URL `'https://api.example.com/data'`로 요청을 보냅니다. 반환되는 Promise 객체는 `then`으로 처리되며, 이 때의 `response`는 `Response` 객체입니다. 이 객체의 `.json()` 메서드를 호출하여 JSON 데이터를 얻습니다.

## 결론: 정확한 이해와 활용이 중요

`fetch` 함수가 반환하는 객체가 `Response` 객체임을 이해하는 것은 중요합니다. 이 객체를 통해 HTTP 응답을 정확히 처리하고, 여러 가지 추가 작업을 수행할 수 있습니다. 이러한 이해를 바탕으로 `fetch` 함수를 더 효과적으로 활용할 수 있을 것입니다.
