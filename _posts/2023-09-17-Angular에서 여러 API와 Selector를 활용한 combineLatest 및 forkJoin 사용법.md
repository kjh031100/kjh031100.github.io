---
title: Angular에서 여러 API와 Selector를 활용한 combineLatest 및 forkJoin 사용법
date: 2023-09-17 20:00:00 +0900
categories:
  - JavaScript
tags:
  - 자바스크립트
  - Angular
---

## 개요

Angular에서 다수의 API 호출을 병렬로 처리하고, 그 결과를 하나의 객체나 배열로 합치는 방법에 대해서 다룹니다. 이 때 사용되는 RxJS 연산자인 `combineLatest`와 `forkJoin`에 대한 설명과 이들을 선택기(selector)와 함께 어떻게 사용할 수 있는지에 대해 알아보겠습니다.

## combineLatest와 forkJoin의 기본 사용법

### combineLatest

`combineLatest`는 여러 옵저버블(observable)이 방출하는 마지막 값을 합쳐서 새로운 값을 만듭니다. 이 연산자는 하나라도 새로운 값을 방출하면 결과를 내보냅니다.

```typescript
combineLatest([obs1$, obs2$, obs3$]).subscribe(([data1, data2, data3]) => {
  // 로직 처리
});
```

### forkJoin

`forkJoin`은 모든 옵저버블이 완료될 때까지 기다린 후, 마지막 값을 합쳐서 결과를 내보냅니다.

```typescript
forkJoin([obs1$, obs2$, obs3$]).subscribe(([data1, data2, data3]) => {
  // 로직 처리
});
```

## 선택기(Selector)와의 조합

선택기는 여러 API 응답을 원하는 형태로 가공할 수 있는 함수입니다. `combineLatest`나 `forkJoin`과 함께 사용되어 결과값을 적절하게 가공할 수 있습니다.

```typescript
combineLatest([obs1$, obs2$, obs3$], (data1, data2, data3) => {
  return { data1, data2, sum: data1 + data2 + data3 };
}).subscribe(result => {
  // 로직 처리
});
```

## 주의사항 및 에러 처리

### `TypeError: You provided an invalid object where a stream was expected`

이 에러는 옵저버블이 아닌 객체를 `combineLatest`나 `forkJoin`에 전달했을 때 발생합니다. 옵저버블 생성을 확인해야 합니다.

### `subscribe` 메서드 내에서의 에러 처리

`subscribe` 메서드 내부에서 `error` 콜백을 활용해 에러를 처리할 수 있습니다.

```typescript
combineLatest([obs1$, obs2$, obs3$]).subscribe({
  next: data => {},
  error: err => {
    console.error(err);
  }
});
```

## 결론

Angular에서 `combineLatest`와 `forkJoin` 연산자를 효율적으로 사용하면 여러 API를 병렬로 호출하고 그 결과를 통합할 수 있습니다. 선택기를 활용하면 더욱 효율적인 데이터 처리가 가능합니다. 에러 발생 시, 주의해야 할 점과 그에 대한 해결 방안도 알아보았습니다. 이를 통해 더욱 견고한 Angular 애플리케이션을 개발할 수 있습니다.