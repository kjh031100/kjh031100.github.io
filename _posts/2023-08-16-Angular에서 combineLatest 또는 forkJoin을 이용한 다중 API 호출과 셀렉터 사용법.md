---
title: Angular에서 combineLatest 또는 forkJoin을 이용한 다중 API 호출과 셀렉터 사용법
date: 2023-08-16 20:00:00 +0900
categories:
  - JavaScript
tags:
  - combineLatest
---

## 문제 상황: 다중 API 호출과 셀렉터 이해하기

질문자는 Angular에서 `combineLatest`와 `forkJoin`을 이용하여 여러 API를 동시에 호출하는 방법에 대해 논의하고 있습니다. 특히, 이 두 연산자를 사용하여 API 데이터를 합치고 필터링하는 과정에서 셀렉터(selector)를 어떻게 사용하는지 궁금해합니다.

## `combineLatest`와 `forkJoin`의 차이점

먼저 `combineLatest`와 `forkJoin`의 기본적인 차이점을 알아봅시다. `combineLatest`는 여러 옵저버블(observable) 스트림이 업데이트될 때마다 마지막 값들을 조합하여 새로운 값을 생성합니다. 반면, `forkJoin`은 모든 옵저버블이 완료되면 마지막 값을 반환합니다. 

## 셀렉터(selector)란?

셀렉터는 `combineLatest`나 `forkJoin` 같은 연산자에서 여러 옵저버블의 값을 합치거나 필터링하는 함수입니다. 이것을 통해 복잡한 데이터 로직을 캡슐화할 수 있습니다.

## 다중 API 호출과 셀렉터 사용 예제

Angular의 `HttpClient` 모듈과 `RxJS` 라이브러리를 사용하여 간단한 예제를 살펴봅시다.

```typescript
import { combineLatest } from 'rxjs';
import { HttpClient } from '@angular/common/http';

constructor(private http: HttpClient) { }

getData() {
  const api1$ = this.http.get('https://api1.com/data');
  const api2$ = this.http.get('https://api2.com/data');

  combineLatest([api1$, api2$], (data1, data2) => {
    return { ...data1, ...data2 };
  }).subscribe(combinedData => {
    console.log('결과:', combinedData);
  });
}
```

위 코드는 `api1`과 `api2`에서 데이터를 가져온 후 셀렉터를 사용하여 두 데이터를 합칩니다. 

## 에러 처리: `TypeError`

만약 다중 API 호출 중에 하나가 실패한다면 `TypeError`가 발생할 수 있습니다. 이를 해결하기 위해서는 `catchError` 연산자를 사용할 수 있습니다.

## 마무리

`combineLatest`와 `forkJoin`을 사용하여 다중 API 호출을 쉽게 관리할 수 있습니다. 셀렉터를 이용하면 더욱 효과적으로 데이터를 조작할 수 있습니다. 이를 통해 Angular에서 더욱 강력한 데이터 처리가 가능합니다.