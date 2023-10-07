---
title: 미니 힙 정렬 (Mini Heap Sort) 구현 방법 in JavaScript
date: 2023-08-17 20:00:00 +0900
categories:
  - JavaScript
tags:
  - Heap
---

## 정렬 알고리즘의 이해

힙 정렬(Heap Sort)은 컴퓨터 과학에서 중요하게 다루는 정렬 알고리즘 중 하나입니다. 미니 힙 정렬은 힙 정렬의 변형 버전으로 볼 수 있습니다. 알고리즘(Algorithm)이란 문제를 해결하기 위한 단계별 방법을 의미합니다.

## 힙 정렬과 미니 힙 정렬의 차이

힙 정렬은 완전 이진 트리 구조를 사용하여 정렬을 수행하는 반면, 미니 힙 정렬은 일반적으로 부분적으로 정렬된 데이터에 대해 더 효율적으로 작동합니다. 완전 이진 트리(Complete Binary Tree)는 모든 레벨이 꽉 찬 이진 트리를 말합니다.

## JavaScript에서의 구현

JavaScript에서 미니 힙 정렬을 구현하기 위해서는 다음과 같은 주요 함수가 필요합니다:

1. `heapify`: 배열을 힙 구조로 만드는 함수
2. `buildHeap`: 초기 힙을 구성하는 함수
3. `heapSort`: 힙을 이용해서 배열을 정렬하는 함수

### `heapify` 함수

```javascript
function heapify(arr, n, i) {
  let largest = i;
  let left = 2 * i + 1;
  let right = 2 * i + 2;

  if (left < n && arr[left] > arr[largest]) {
    largest = left;
  }

  if (right < n && arr[right] > arr[largest]) {
    largest = right;
  }

  if (largest !== i) {
    [arr[i], arr[largest]] = [arr[largest], arr[i]];
    heapify(arr, n, largest);
  }
}
```

### `buildHeap` 함수

```javascript
function buildHeap(arr, n) {
  for (let i = Math.floor(n / 2) - 1; i >= 0; i--) {
    heapify(arr, n, i);
  }
}
```

### `heapSort` 함수

```javascript
function heapSort(arr) {
  const n = arr.length;
  buildHeap(arr, n);

  for (let i = n - 1; i > 0; i--) {
    [arr[0], arr[i]] = [arr[i], arr[0]];
    heapify(arr, i, 0);
  }
}
```

이러한 함수들을 이용하면, 미니 힙 정렬을 JavaScript로 구현할 수 있습니다. 이 코드를 이해하고 활용하면 더 효율적인 데이터 정렬이 가능해집니다.