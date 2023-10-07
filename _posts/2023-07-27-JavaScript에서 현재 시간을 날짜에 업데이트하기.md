---
title: JavaScript에서 현재 시간을 날짜에 업데이트하기
date: 2023-07-27 20:00:00 +0900
categories:
  - JavaScript
tags:
  - JavaScript시간
---

## 문제 상황 소개

개발자들은 자주 웹 페이지나 앱에서 현재 시간을 표시해야 하는 경우가 있습니다. 이러한 경우에 JavaScript를 이용해서 현재 시간을 쉽게 구하고 업데이트할 수 있습니다. 하지만, 이 과정에서 'Uncaught TypeError' 같은 에러를 마주칠 수도 있습니다. 이 글에서는 이와 관련된 문제를 해결하는 방법을 자세히 설명하겠습니다.

## Uncaught TypeError 해결 방법

Uncaught TypeError는 변수나 함수를 잘못 사용했을 때 자주 발생하는 에러입니다. 이 에러를 해결하기 위해서는 코드의 문법과 로직을 철저히 검토해야 합니다. 아래는 예시 코드입니다.

```javascript
let date = new Date();
document.getElementById("time").innerHTML = date.getHours() + ":" + date.getMinutes() + ":" + date.getSeconds();
```

이 코드를 실행하면 웹 페이지에 있는 "time"이라는 ID를 가진 요소에 현재 시간이 표시됩니다.

## 시간 업데이트 자동화하기

단순히 한 번 시간을 표시하는 것보다는 자동으로 업데이트되는 시간을 표시하는 것이 더 유용합니다. 이를 위해 `setInterval` 함수를 사용할 수 있습니다.

```javascript
function updateTime() {
  let date = new Date();
  document.getElementById("time").innerHTML = date.getHours() + ":" + date.getMinutes() + ":" + date.getSeconds();
}

setInterval(updateTime, 1000);
```

`setInterval` 함수는 첫 번째 인자로 주어진 함수를 두 번째 인자로 주어진 시간 간격으로 반복해서 실행합니다. 위 코드에서는 `updateTime` 함수를 1초(1000밀리초)마다 반복해서 실행하도록 설정했습니다.

## 요약

JavaScript를 이용하여 현재 시간을 웹 페이지에 표시하고 업데이트하는 것은 복잡하지 않습니다. `Date` 객체와 `getElementById`, 그리고 `setInterval` 함수를 이용하면 간단하게 해결할 수 있습니다. 이 글을 통해 Uncaught TypeError 같은 에러 없이 원활하게 시간을 표시하고 업데이트할 수 있게 되었길 바랍니다.