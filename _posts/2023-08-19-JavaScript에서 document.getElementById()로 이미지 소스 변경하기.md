---
title: JavaScript에서 document.getElementById()로 이미지 소스 변경하기
date: 2023-08-19 20:00:00 +0900
categories:
  - JavaScript
tags:
  - 이미지소스변경
---

## 문제 상황: `Uncaught TypeError: Cannot set properties of null`

JavaScript를 사용하여 HTML의 이미지 소스를 동적으로 변경하고자 했을 때, StackOverflow에서 본 문제는 `Uncaught TypeError: Cannot set properties of null` 이라는 오류가 발생하는 것입니다. 이 오류는 요소가 페이지에서 찾지 못할 때 발생합니다.

## 원인 분석: 페이지 로딩 시점

이 오류는 대부분 자바스크립트 코드가 HTML 페이지가 완전히 로드되기 전에 실행되어 요소를 찾지 못하기 때문에 발생합니다. 이 때문에 `null` 값을 반환하고, 이후에 속성을 변경하려 하면 오류가 발생합니다.

## 해결 방법: `DOMContentLoaded` 이벤트 사용하기

이 문제를 해결하기 위한 가장 흔한 방법은 `DOMContentLoaded` 이벤트를 사용하는 것입니다. 이 이벤트는 HTML 문서가 완전히 로드된 후에 실행됩니다.

```javascript
document.addEventListener("DOMContentLoaded", function() {
  var imgSrc = "your-image-url-here";
  document.getElementById("your-image-id").src = imgSrc;
});
```

## 추가 팁: `window.onload` 사용하기

`window.onload` 이벤트를 사용하는 것도 가능한 해결책입니다. 이 이벤트는 모든 리소스가 로드된 이후에 실행되므로, 스크립트 로딩이 느려질 가능성이 있지만 더 안정적입니다.

```javascript
window.onload = function() {
  var imgSrc = "your-image-url-here";
  document.getElementById("your-image-id").src = imgSrc;
};
```

## 이미지 소스를 변수로 설정하기

`imgSrc` 변수에 원하는 이미지의 URL을 지정하면 됩니다. 이 변수 값을 변경함으로써 동적으로 이미지를 교체할 수 있습니다.

## 정리

- `Uncaught TypeError: Cannot set properties of null` 오류는 요소를 찾지 못할 때 발생합니다.
- `DOMContentLoaded` 또는 `window.onload` 이벤트를 사용하여 문제를 해결할 수 있습니다.
- 변수를 사용하여 이미지 소스를 동적으로 변경할 수 있습니다.

이러한 방법을 통해 HTML 페이지에서 자바스크립트를 이용해 이미지 소스를 동적으로 변경하는 문제를 쉽게 해결할 수 있습니다.