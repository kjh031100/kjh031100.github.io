---
title: 파일 다이얼로그 열기 input type=button 이용하기
date: 2023-08-03 20:00:00 +0900
categories:
  - JavaScript
tags:
  - 인풋타입
---

## 문제 상황 설명

사용자가 웹 페이지에서 버튼을 클릭하면 파일 선택 창을 열고 싶다는 것이 문제의 핵심입니다. 이 작업은 보통 `<input type="file">`을 이용해 수행되지만, 여기서는 `input type=button`을 이용하고 싶다고 합니다.

## 해결 방법

이 문제를 해결하는 가장 간단한 방법은 자바스크립트를 사용하는 것입니다. `input type=button` 버튼을 클릭하면, 자바스크립트 코드를 실행해 `<input type="file">`을 간접적으로 클릭하는 것이죠. 이를테면 다음과 같은 코드를 사용할 수 있습니다.

```javascript
// HTML 부분
<input type="button" value="파일 열기" id="openFile">
<input type="file" id="fileInput" style="display:none">

// 자바스크립트 부분
document.getElementById('openFile').addEventListener('click', function() {
  document.getElementById('fileInput').click();
});
```

## 코드 분석

- `style="display:none"`: 이 코드는 `<input type="file">`을 보이지 않게 만듭니다.
- `addEventListener('click', function() {})`: 이 코드는 버튼 클릭 시 특정 함수를 실행하도록 설정합니다.
- `document.getElementById('fileInput').click();`: 이 코드는 실제 파일 선택 창을 엽니다.

자바스크립트는 웹 페이지의 동적인 요소를 다루는 데 아주 유용합니다. 이 코드 예시에서도 자바스크립트가 웹 페이지에서 사용자의 액션에 따라 다른 요소를 제어하고 있음을 볼 수 있습니다.

## 주의 사항

이 방법은 브라우저가 자바스크립트를 지원해야만 작동합니다. 자바스크립트가 비활성화된 상태에서는 이 코드가 작동하지 않을 것입니다. 그리고 이 방법은 보안상의 문제가 없으므로 안전하게 사용할 수 있습니다.

## 결론

`input type=button`을 이용해서 파일 선택 다이얼로그를 열려면, 간단한 자바스크립트 코드 몇 줄로 이를 해결할 수 있습니다. 이 방법은 특별한 의존성 없이도 구현 가능하며, 다양한 웹 브라우저에서 잘 작동합니다.