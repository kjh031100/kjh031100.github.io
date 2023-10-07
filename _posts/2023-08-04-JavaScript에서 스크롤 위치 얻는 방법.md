---
title: JavaScript에서 스크롤 위치 얻는 방법
date: 2023-08-04 20:00:00 +0900
categories:
  - JavaScript
tags:
  - 스크롤위치
---

## 개요
스크롤 위치를 얻어내는 것은 웹 개발에서 자주 마주치는 작업입니다. 여기서는 CSS만을 사용해서 스크롤 위치를 얻는 것은 불가능하다는 사실과, 그 대신 어떻게 이를 구현할 수 있는지에 대해 알아보겠습니다.

## CSS만으로는 불가능하다
CSS는 스타일링 언어로, 웹 페이지의 요소들에게 스타일을 적용하는 것이 주 목적입니다. 스크롤 위치 같은 동적인 정보를 가져오는 것은 CSS의 기능 범위를 벗어납니다. 이를 위해서는 보통 JavaScript를 사용합니다.

## JavaScript를 활용한 방법
JavaScript에서는 `window.scrollY` 또는 `window.pageYOffset` 속성을 사용해서 현재의 스크롤 위치를 얻을 수 있습니다. 이 값은 페이지의 맨 위에서부터 현재 보이는 화면까지의 거리를 픽셀 단위로 나타냅니다. 

```javascript
let scrollPosition = window.scrollY;
```

위의 코드를 실행하면 `scrollPosition` 변수에 현재 스크롤 위치가 저장됩니다.

## 스크롤 이벤트와 함께 사용하기
스크롤 위치에 따라 어떤 동작을 실행하고 싶다면, `scroll` 이벤트를 사용할 수 있습니다.

```javascript
window.addEventListener('scroll', function() {
    let scrollPosition = window.scrollY;
    // 여기에 스크롤 위치에 따른 동작을 코딩합니다.
});
```

이렇게 하면 사용자가 스크롤할 때마다 이벤트가 발생하고, 그에 따른 작업을 수행할 수 있습니다.

## 결론
CSS만으로 스크롤 위치를 얻는 것은 불가능합니다. 이러한 작업은 JavaScript를 통해 구현할 수 있으며, `window.scrollY`나 `scroll` 이벤트를 사용해서 더 다양한 동작을 만들 수 있습니다. CSS와 JavaScript를 적절히 조합하면 사용자 경험을 향상시키는 다양한 기능을 구현할 수 있습니다.