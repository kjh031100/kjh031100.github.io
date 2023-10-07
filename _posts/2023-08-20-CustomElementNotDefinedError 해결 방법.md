---
title: CustomElementNotDefinedError 해결 방법
date: 2023-08-20 20:00:00 +0900
categories:
  - JavaScript
tags:
  - 자바스크립트에러
---

## 문제 상황: `CustomElementNotDefinedError`

해당 Stack Overflow 질문에서 사용자는 커스텀 HTML 요소를 화면에 렌더링하려고 시도했습니다. 하지만 문제가 발생했으며, 개발자 도구에서는 `CustomElementNotDefinedError`라는 에러 메시지를 확인할 수 있었습니다.

## 원인: 렌더링 순서와 정의 누락

1. **렌더링 순서**: 브라우저는 HTML 파일을 위에서 아래로 해석합니다. 커스텀 요소가 정의되기 전에 사용되면, 브라우저는 그것을 일반적인 HTML 태그로 취급합니다.

2. **정의 누락**: 커스텀 요소를 생성할 때 `customElements.define()` 함수를 사용해야 합니다. 이 함수를 사용하지 않으면 브라우저는 커스텀 요소를 알 수 없습니다.

## 해결 방법: 코드 순서와 정의 확인

### 코드 순서 조정
커스텀 요소를 정의하는 코드를 HTML 문서의 상단에 배치하여 렌더링 순서를 조정하세요. 이렇게 하면 브라우저가 커스텀 요소를 올바르게 해석할 수 있습니다.

### 정의 추가
`customElements.define()` 함수를 사용하여 커스텀 요소를 명시적으로 정의하세요. 이 함수는 첫 번째 매개변수로 커스텀 요소의 이름, 두 번째 매개변수로 클래스를 받습니다.

```javascript
customElements.define('my-custom-element', MyCustomElementClass);
```

## 예제: 올바른 커스텀 요소 생성

HTML 파일:

```html
<!DOCTYPE html>
<html>
<head>
    <script src="my-custom-element.js"></script>
</head>
<body>
    <my-custom-element></my-custom-element>
</body>
</html>
```

JavaScript 파일 (`my-custom-element.js`):

```javascript
class MyCustomElementClass extends HTMLElement {
    constructor() {
        super();
        // 로직 추가
    }
}

customElements.define('my-custom-element', MyCustomElementClass);
```

이렇게 하면 `CustomElementNotDefinedError` 문제를 해결하고 커스텀 요소를 올바르게 렌더링할 수 있습니다.