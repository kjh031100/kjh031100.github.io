---
title: 동적으로 TypeScript에서 객체 속성 할당하기
date: 2023-05-29 20:00:00 +0900
categories:
  - TypeScript
tags:
  - TypeScript객체
---

## 문제 정의: TypeScript에서의 동적 속성 할당

JavaScript에서는 객체에 동적으로 속성을 추가할 수 있습니다. 그러나 TypeScript에서는 미리 정의된 인터페이스나 클래스에 따라 작동하기 때문에, 이를 할 때 문제가 생길 수 있습니다. 어떻게 해결할 수 있을까요?

## 해결책 1: 인덱스 시그니처(Index Signature) 사용하기

TypeScript에서 객체에 동적으로 속성을 추가하려면 인덱스 시그니처를 사용할 수 있습니다. 인덱스 시그니처란 객체의 가능한 키와 그 키에 할당될 값의 타입을 정의하는 방법입니다.

```typescript
interface DynamicObject {
  [key: string]: any;
}

const obj: DynamicObject = {};
obj["newKey"] = "newValue";
```

위 코드에서 `DynamicObject`는 문자열 키와 어떤 타입의 값도 받을 수 있는 인덱스 시그니처를 가지고 있습니다.

## 해결책 2: `Object.assign()` 메서드 사용하기

JavaScript의 `Object.assign()` 메서드를 이용하면, 존재하는 객체에 새로운 속성을 추가할 수 있습니다.

```typescript
const obj = { key1: "value1" };
Object.assign(obj, { key2: "value2" });
```

위 코드는 `obj`에 `key2`라는 새로운 속성을 `value2` 값으로 추가합니다.

## 해결책 3: 스프레드 연산자(Spread Operator) 활용하기

스프레드 연산자를 이용하면, 존재하는 객체의 모든 속성을 새로운 객체에 복사한 뒤, 새로운 속성을 추가할 수 있습니다.

```typescript
const obj = { key1: "value1" };
const newObj = { ...obj, key2: "value2" };
```

## 주의사항: Strict Mode에서의 동적 할당

TypeScript의 `strict` 모드에서는 더 엄격한 타입 검사를 수행합니다. 따라서, 위의 방법들은 `strict` 모드에서 작동하지 않을 수 있으므로 주의가 필요합니다.

## 결론

TypeScript에서 객체에 동적으로 속성을 추가하는 것은 JavaScript보다 복잡할 수 있지만, 인덱스 시그니처, `Object.assign()` 메서드, 스프레드 연산자 등 다양한 방법을 활용하면 문제를 해결할 수 있습니다.