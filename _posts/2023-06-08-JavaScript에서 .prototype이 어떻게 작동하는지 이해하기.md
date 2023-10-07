---
title: JavaScript에서 .prototype이 어떻게 작동하는지 이해하기
date: 2023-06-08 20:00:00 +0900
categories:
  - JavaScript
tags:
  - prototype
---

## .prototype의 개념

JavaScript에서 모든 객체는 null 또는 객체 값을 가진 내부 "슬롯"인 [ [Prototype]]을 가지고 있습니다. 이는 객체가 생성될 때 생성자의 “prototype” 속성을 참조하는 객체에서 직접 메서드와 속성에 접근할 수 있게 합니다. 객체의 프로토타입(따라서 상속된 속성 이름)은 Object.getPrototypeOf() 메서드를 사용하여 검색할 수 있습니다.

## 클래스 기반 언어와의 차이점

Java, C# 또는 C++와 같은 클래스 기반 상속을 구현하는 언어에서는 먼저 클래스(객체의 청사진)를 생성하고, 그 클래스에서 새로운 객체를 생성하거나 클래스를 확장하여 원래 클래스를 보강하는 새로운 클래스를 정의할 수 있습니다. JavaScript에서는 먼저 객체를 생성하고(클래스 개념이 없음), 자신의 객체를 보강하거나 새로운 객체를 생성할 수 있습니다.

## 예제

다음은 JavaScript에서 'Person’이라는 함수형 객체를 정의하는 예제입니다:

```javascript
var Person = function (name) {
  this.name = name;
};
```

이미 정의된 객체에 새로운 getter를 동적으로 추가할 수 있습니다:

```javascript
Person.prototype.getName = function () {
  return this.name;
};
```

‘Person’ 타입의 새로운 객체를 생성해봅시다:

```javascript
var john = new Person ("John");
```

getter를 시도해봅시다:

```javascript
alert (john.getName ());
```

이제 'Person’을 수정하면, 'john’도 업데이트를 받게 됩니다:

```javascript
Person.prototype.sayMyName = function () {
  alert ('Hello, my name is ' + this.getName ());
};
```

'john’에 대해 새로운 메서드를 호출해봅시다:

```javascript
john.sayMyName ();
```

## 결론

JavaScript에서 .prototype은 매우 중요한 개념입니다. 이는 객체 지향 프로그래밍에서 상속을 가능하게 하며, 특히 프로토타입 기반 언어인 JavaScript에서 중요한 역할을 합니다. 이를 이해하고 올바르게 사용하면, 코드 재사용성을 높이고 유지 관리를 용이하게 할 수 있습니다.