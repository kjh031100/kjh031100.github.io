---
title: 자바스크립트의 Conditional Compilation 오류 해결 방법
date: 2023-07-02 20:00:00 +0900
categories:
  - JavaScript
tags:
  - 자바스크립트오류
---

## 오류 상황: Conditional Compilation is turned off

'Conditional Compilation'은 주로 Internet Explorer에서 사용되는 자바스크립트의 특수한 기능입니다. 이 오류는 Internet Explorer 외의 브라우저에서 발생할 가능성이 높습니다. 오류 메시지는 대체로 "Conditional Compilation is turned off"라고 표시됩니다.

## 해결 방법 1: @cc_on 지시어 사용

첫 번째 방법은 `@cc_on`이라는 지시어를 사용하는 것입니다. 이 지시어는 'Conditional Compilation'이 활성화되어 있는지 확인합니다. 다음과 같이 코드에 추가할 수 있습니다.

```javascript
/*@cc_on @*/
/*@if (@_jscript)
  // Internet Explorer에서만 실행될 코드
@end @*/
```

'지시어'란 컴파일러나 인터프리터에게 어떤 작업을 수행하도록 지시하는 명령어입니다.

## 해결 방법 2: 자바스크립트 조건문 활용

두 번째 방법은 일반 자바스크립트의 조건문을 사용하여 브라우저를 확인하는 것입니다. 이렇게 하면 다른 브라우저에서도 문제 없이 코드가 실행됩니다.

```javascript
if (navigator.userAgent.indexOf('MSIE') !== -1 || navigator.appVersion.indexOf('Trident/') > -1) {
  // Internet Explorer에서만 실행될 코드
}
```

'조건문'이란 특정 조건이 참인지 거짓인지 판단하여 코드의 실행 흐름을 제어하는 구문입니다.

## 해결 방법 3: 메타 태그 설정 변경

세 번째 방법은 HTML 문서의 `<head>` 부분에 메타 태그를 추가하는 것입니다. 다음과 같이 코드를 삽입하면 'Conditional Compilation'이 활성화됩니다.

```html
<meta http-equiv="X-UA-Compatible" content="IE=edge" />
```

'메타 태그'는 웹 문서에 대한 메타데이터를 정의하는 HTML 태그입니다. 메타데이터는 데이터를 설명하는 데이터입니다.

이렇게 세 가지 방법을 적용하면 'Conditional Compilation' 오류를 효과적으로 해결할 수 있습니다. 어떤 방법이 가장 적합한지는 사용하고 있는 브라우저와 개발 환경에 따라 다를 수 있습니다. 따라서 여러 가지 방법을 시도하여 가장 적합한 해결책을 찾아보는 것이 좋습니다.