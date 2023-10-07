---
title: 자바스크립트에서 Hidden JavaScript Error 해결하기
date: 2023-06-27 20:00:00 +0900
categories:
  - JavaScript
tags:
  - 자바스크립트오류
---

## 에러 현상 및 원인

스택오버플로우에 올라온 글에서 말하는 'Hidden JavaScript Error'는 코드를 실행할 때 눈에 보이지 않는 자바스크립트 에러를 의미합니다. 이 에러는 콘솔에서도 명확하게 표시되지 않아, 문제를 진단하기 어렵습니다. 대표적으로 이러한 에러가 발생하는 원인은 다음과 같습니다.

1. 비동기(asynchronous) 코드에서 발생하는 에러: `setTimeout` 또는 `setInterval`과 같은 비동기 함수에서 발생하는 에러입니다.
2. 이벤트 핸들러(event handler)에서의 에러: 클릭, 터치, 키보드 입력 등의 이벤트를 다루는 코드에서 에러가 발생할 수 있습니다.

## 해결 방안

### 비동기 코드에서의 에러 처리

비동기 코드에서 에러가 발생하면, `try`와 `catch` 구문을 이용해 에러를 잡아냅니다. 또는, 비동기 코드의 콜백 함수(callback function)에서 `.catch()` 메서드를 이용해 에러를 처리할 수 있습니다.

```javascript
setTimeout(() => {
  try {
    // 여기에 코드 작성
  } catch (error) {
    console.error("An error occurred: ", error);
  }
}, 1000);
```

### 이벤트 핸들러에서의 에러 처리

이벤트 핸들러에서 발생하는 에러는 해당 이벤트를 감지하는 함수 내에서 `try`와 `catch` 구문을 사용해 처리합니다.

```javascript
button.addEventListener("click", () => {
  try {
    // 여기에 코드 작성
  } catch (error) {
    console.error("An error occurred: ", error);
  }
});
```

## 요약 및 마무리

'Hidden JavaScript Error'는 자바스크립트에서 쉽게 발견되지 않는 에러입니다. 이를 해결하기 위해서는 비동기 코드와 이벤트 핸들러에서 각각 `try`와 `catch` 구문을 활용해야 합니다. 이를 통해 코드의 안정성을 높일 수 있습니다.