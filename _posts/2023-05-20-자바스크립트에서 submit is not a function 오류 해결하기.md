---
title: 자바스크립트에서 submit is not a function 오류 해결하기
date: 2023-05-20 20:00:00 +0900
categories:
  - JavaScript
tags:
  - 자바스크립트오류
---

## 오류 상황 파악

웹 페이지에서 폼을 제출하려고 할 때 자바스크립트에서 "submit is not a function"이라는 오류 메시지가 나타나는 경우가 있습니다. 이 오류 메시지가 뜨면 폼 제출이 제대로 이루어지지 않는 문제가 발생합니다. 이 오류가 왜 발생하는지 그리고 어떻게 해결할 수 있는지 알아봅시다.

## 오류 원인: 이름 충돌

이 오류가 발생하는 가장 일반적인 원인은 HTML 폼의 입력 필드나 버튼의 이름이나 아이디가 "submit"으로 설정되어 있을 때입니다. 원래 자바스크립트에서는 `form.submit()` 메서드를 사용해 폼을 프로그래밍적으로 제출할 수 있습니다. 그런데 폼 내부의 이름이나 아이디가 "submit"인 요소가 있으면, 이 "submit"이 메서드와 충돌하게 되어 오류가 발생합니다.

## 해결 방법 1: 이름 변경하기

가장 간단한 해결 방법은 "submit"이라는 이름이나 아이디를 가진 HTML 요소의 이름을 변경하는 것입니다. 예를 들어, 아이디를 "submit_button"으로 바꾸면 이 문제를 쉽게 해결할 수 있습니다.

```html
<!-- 변경 전 -->
<button id="submit" name="submit">제출</button>

<!-- 변경 후 -->
<button id="submit_button" name="submit_button">제출</button>
```

## 해결 방법 2: 메서드 호출 방식 변경하기

만약 이름을 변경할 수 없는 상황이라면, 폼 제출을 다른 방식으로 처리할 수도 있습니다. `document.forms` 배열을 사용하여 폼을 선택하고, `submit` 메서드를 호출하는 방법입니다.

```javascript
document.forms[0].submit();
```

이렇게 하면 "submit"이라는 이름이나 아이디와 충돌하지 않고 폼을 제출할 수 있습니다.

## 정리

"submit is not a function" 오류는 폼의 요소와 메서드 이름이 충돌할 때 발생합니다. 이 문제를 해결하기 위해서는 충돌하는 이름을 변경하거나 다른 방식으로 폼을 제출해야 합니다. 이 두 가지 방법 중 하나를 적용하면 웹 페이지에서 폼을 원활하게 제출할 수 있습니다.