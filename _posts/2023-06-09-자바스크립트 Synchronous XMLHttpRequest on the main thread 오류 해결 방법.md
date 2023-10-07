---
title: 자바스크립트 Synchronous XMLHttpRequest on the main thread 오류 해결 방법
date: 2023-06-09 20:00:00 +0900
categories:
  - JavaScript
tags:
  - 자바스크립트오류
---

## 오류의 정의와 원인

먼저, `Synchronous XMLHttpRequest on the main thread`라는 오류는 웹 브라우저에서 자바스크립트로 XML HTTP 요청을 동기적으로 실행할 때 발생합니다. 이러한 동기적 요청은 사용자 경험을 저하시키고, 브라우저가 멈춰버릴 수도 있기 때문에 권장되지 않습니다.

## 해결 방법 1: 비동기 요청 사용

가장 일반적인 해결 방법은 동기적 요청을 비동기적 요청으로 변경하는 것입니다. 아래는 기존 코드를 비동기로 변경하는 예시입니다.

```javascript
// 동기적 코드
var xhr = new XMLHttpRequest();
xhr.open('GET', 'https://api.example.com/data', false);
xhr.send();

// 비동기적 코드
var xhr = new XMLHttpRequest();
xhr.open('GET', 'https://api.example.com/data', true);
xhr.send();
```

여기서 `true`를 설정하면 요청이 비동기적으로 처리됩니다.

## 해결 방법 2: 메인 스레드 외부에서 처리

웹 워커(Web Worker)를 사용하여 메인 스레드 외부에서 동기적인 XML HTTP 요청을 실행할 수 있습니다. 웹 워커는 백그라운드에서 실행되므로 사용자 인터페이스에 영향을 미치지 않습니다.

```javascript
// 웹 워커 코드 예시
var xhr = new XMLHttpRequest();
xhr.open('GET', 'https://api.example.com/data', false);
xhr.send();
```

## 주의사항

비동기적 요청을 사용하더라도 서버 응답을 기다리는 동안 다른 코드가 실행될 수 있으므로, 콜백 함수나 프로미스(Promise)를 사용하여 서버 응답을 제대로 처리해야 합니다.

```javascript
var xhr = new XMLHttpRequest();
xhr.open('GET', 'https://api.example.com/data', true);
xhr.onreadystatechange = function() {
  if (xhr.readyState == 4 && xhr.status == 200)
    console.log(JSON.parse(xhr.responseText));
}
xhr.send();
```

이렇게 하면 `Synchronous XMLHttpRequest on the main thread` 오류를 효과적으로 해결할 수 있습니다.