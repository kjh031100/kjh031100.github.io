---
title: JavaScript에서 변수를 사용해 img 태그의 src 속성 설정하기
date: 2023-09-20 20:00:00 +0900
categories:
  - JavaScript
tags:
  - 자바스크립트
  - img태그
---

## 문제 상황

개발자들이 자주 마주치는 문제 중 하나는 JavaScript에서 `img` 태그의 `src` 속성을 동적으로 변경하는 것입니다. 주로 `document.getElementById` 메소드를 사용해서 이 작업을 처리하곤 합니다. 이 문제는 특히 웹 개발에서 이미지를 동적으로 로드해야 할 필요가 있을 때 자주 발생합니다.

## 해결 방법: `document.getElementById`와 `src` 속성 사용하기

JavaScript에서 `img` 태그의 `src` 속성을 동적으로 변경하는 가장 간단한 방법은 `document.getElementById` 함수를 사용하여 해당 요소를 선택한 다음, `src` 속성을 변경하는 것입니다.

```javascript
// HTML에서 이미지 요소 선택
var imgElement = document.getElementById("myImage");

// 이미지 URL을 변수에 저장
var imageUrl = "https://example.com/image.jpg";

// src 속성 변경
imgElement.src = imageUrl;
```

이 코드는 "myImage"라는 `id` 속성을 가진 `img` 태그의 `src` 속성을 "https://example.com/image.jpg"로 변경합니다.

## 주의사항: 에러와 디버깅

코드를 실행하면서 다음과 같은 에러를 마주칠 수 있습니다.

- `TypeError: Cannot set properties of null (setting 'src')`

이 에러는 `document.getElementById` 함수가 `null` 값을 반환했다는 것을 의미합니다. 이는 "myImage"라는 `id`를 가진 `img` 요소를 찾지 못했다는 뜻입니다. 이 경우, HTML 코드를 확인하여 `id` 속성이 올바르게 설정되어 있는지 확인해야 합니다.

## 결론

JavaScript에서 `img` 태그의 `src` 속성을 동적으로 설정하는 작업은 `document.getElementById` 메소드를 통해 간단하게 해결할 수 있습니다. 코드를 작성할 때 주의해야 할 주요 에러는 `TypeError: Cannot set properties of null (setting 'src')`입니다. 이 에러는 대게 `id` 속성이 잘못 설정되었을 때 발생하므로, HTML 코드를 잘 확인해야 합니다. 이렇게 하면 웹 페이지에서 이미지를 더 유동적으로 다룰 수 있습니다.