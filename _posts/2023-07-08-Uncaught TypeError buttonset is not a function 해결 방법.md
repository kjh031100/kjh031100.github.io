---
title: Uncaught TypeError buttonset is not a function 해결 방법
date: 2023-07-08 20:00:00 +0900
categories:
  - JavaScript
tags:
  - 타입스크립트에러
---


jQuery UI를 사용하면서 발생하는 `Uncaught TypeError: $(...).buttonset is not a function` 오류는 꽤 흔하게 볼 수 있는 문제입니다. 이 오류가 나타나는 이유와 해결책에 대해 자세하게 알아보겠습니다.

## 오류 원인 파악

이 오류가 발생하는 주된 이유는 jQuery UI 라이브러리가 제대로 로드되지 않았거나, 또는 중복되어 로드되는 경우입니다. 라이브러리는 프로그래밍에서 특정 기능을 쉽게 사용할 수 있도록 미리 만들어진 코드 조각입니다. 이런 라이브러리가 제대로 작동하지 않으면, 우리가 사용하려는 `buttonset` 함수도 동작하지 않게 됩니다.

## 해결책 1: 라이브러리 로드 순서 확인

HTML 파일 내에서 스크립트를 로드할 때, jQuery 라이브러리가 jQuery UI보다 먼저 로드되어야 합니다. 이 순서를 잘못 지정하면 오류가 발생할 수 있습니다. 아래와 같이 순서를 맞춰주세요.

```html
<script src="jquery.min.js"></script>
<script src="jquery-ui.min.js"></script>
```

## 해결책 2: 라이브러리 중복 제거

같은 라이브러리가 두 번 로드되면 오류가 발생할 수 있습니다. HTML 파일을 확인하여 중복 로드를 제거해야 합니다.

## 해결책 3: jQuery 버전 확인

라이브러리 간의 버전 충돌도 오류를 일으킬 수 있습니다. `buttonset` 함수를 사용하려면, 적절한 버전의 jQuery와 jQuery UI를 사용해야 합니다. 버전 정보는 라이브러리의 공식 문서에서 확인할 수 있습니다.

## 결론

`Uncaught TypeError: $(...).buttonset is not a function` 오류는 대체로 라이브러리 로딩 문제에서 비롯됩니다. 로드 순서, 중복, 그리고 버전을 체크하여 이 문제를 해결할 수 있습니다. 이 세 가지 요소를 주의 깊게 확인하면 대부분의 문제는 쉽게 해결될 것입니다.