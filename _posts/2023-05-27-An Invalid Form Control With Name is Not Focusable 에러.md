---
title: An Invalid Form Control With Name is Not Focusable 에러
date: 2023-05-27 20:00:00 +0900
categories:
  - JavaScript
tags:
  - Form에러
---

## 에러의 원인

먼저 이 문제가 어떤 상황에서 발생하는지 이해하는 것이 중요합니다. HTML에서는 `<form>` 태그 내에 다양한 입력 요소를 배치할 수 있습니다. 이러한 입력 요소 중 하나 이상이 유효하지 않을 경우, 이 에러가 발생합니다. 주로 이유는 다음과 같습니다:

1. `required` 속성이 있는데, 값을 입력하지 않았을 때
2. `hidden` 속성이 있어서 사용자가 값을 입력할 수 없는 상태일 때

## 해결책 1: `required` 속성 제거 또는 값 할당

`required` 속성이 문제의 원인일 경우, 이 속성을 제거하거나 해당 필드에 유효한 값을 입력해야 합니다.

### 단계별 가이드

1. `required` 속성이 있는 입력 필드를 찾습니다.
2. 해당 필드에 유효한 값을 할당하거나 `required` 속성을 제거합니다.

```html
<!-- 이전 코드 -->
<input type="text" name="username" required>

<!-- 수정된 코드 -->
<input type="text" name="username">
```

## 해결책 2: `hidden` 속성 처리

`hidden` 속성이 문제라면, 이 속성을 제거하거나 필요한 값을 할당해야 합니다. 

### 단계별 가이드

1. `hidden` 속성이 있는 입력 필드를 찾습니다.
2. 필요한 값으로 할당하거나 `hidden` 속성을 제거합니다.

```html
<!-- 이전 코드 -->
<input type="text" name="secret" hidden>

<!-- 수정된 코드 -->
<input type="text" name="secret" value="assigned_value">
```

이러한 방법을 통해 "An Invalid Form Control With Name is Not Focusable" 에러를 해결할 수 있습니다. 문제가 해결되지 않으면 다른 부분의 코드에 문제가 있는 것이므로, 추가적인 디버깅이 필요할 수 있습니다.