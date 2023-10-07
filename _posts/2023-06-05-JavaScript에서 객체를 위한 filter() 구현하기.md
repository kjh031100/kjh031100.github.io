---
title: JavaScript에서 객체를 위한 filter() 구현하기
date: 2023-06-05 20:00:00 +0900
categories:
  - JavaScript
tags:
  - 자바스크립트객체
---

## 문제 상황

Stack Overflow에 게시된 질문에 따르면, 사용자는 JavaScript에서 객체를 필터링하는 방법에 대해 논의하고 있습니다. 사용자는 ECMAScript 5가 배열 유형에 대한 filter() 프로토타입을 가지고 있지만 객체 유형에는 없다는 것을 이해하고 있습니다 그래서 사용자는 JavaScript에서 객체를 위한 filter()를 어떻게 구현할 수 있는지 묻고 있습니다

## 해결 방법

사용자는 다음과 같은 객체를 가지고 있다고 가정합니다

```javascript
var foo = { bar: "Yes" };
```

그리고 사용자는 객체에서 작동하는 filter()를 작성하려고 합니다

```javascript
Object.prototype.filter = function (predicate) {
  var result = {};
  for (key in this) {
    if (this.hasOwnProperty(key) && !predicate(this[key])) {
      result[key] = this[key];
    }
  }
  return result;
};
```

이 코드는 데모에서 작동하지만, jQuery 1.5와 jQuery UI 1.8.9를 사용하는 사이트에 추가하면 JavaScript 오류가 발생한다고 합니다

## 주의 사항

Stack Overflow의 답변 중 하나에서는 Object.prototype을 확장하는 것이 나쁜 관행이라고 지적하였습니다 대신, 기능을 독립적인 함수로 제공하거나, 이미 Object.keys, Object.assign, Object.is 등이 있는 것처럼 Object의 유틸리티 함수로 제공하는 것이 좋습니다

## 해결책 제안

다음은 reduce와 Object.keys를 사용하여 원하는 필터를 구현하는 방법입니다

```javascript
Object.filter = (obj, predicate) => 
  Object.keys(obj)
    .filter(key => predicate(obj[key]))
    .reduce((res, key) => (res[key] = obj[key], res), {});
```

예제 사용은 다음과 같습니다

```javascript
var scores = { John: 2, Sarah: 3, Janet: 1 };
var filtered = Object.filter(scores, score => score > 1);
console.log(filtered);
```

위 코드에서 predicate는 포함 조건이어야 하므로, Array.prototype.filter가 작동하는 방식과 일치하게 됩니다