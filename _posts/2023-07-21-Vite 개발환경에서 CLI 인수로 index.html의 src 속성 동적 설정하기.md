---
title: Vite 개발환경에서 CLI 인수로 index.html의 src 속성 동적 설정하기
date: 2023-07-21 20:00:00 +0900
categories:
  - JavaScript
tags:
  - CLI인수
  - Index
  - html
---

## 문제 상황: Vite에서 index.html의 src 속성을 CLI 인수로 동적 변경

Vite는 웹 개발을 위한 빠르고 경량한 빌드 도구입니다. 그러나 때로는 개발 중에 CLI(Command Line Interface) 인수를 통해 `index.html` 파일의 `src` 속성을 동적으로 설정해야 할 필요가 있습니다. 예를 들어, 개발과 배포 버전에서 다른 스크립트 파일을 로드해야 할 때가 있습니다. 이 문제는 Stack Overflow에도 여러 번 등장했고, 여러 개발자들이 이에 대한 해결책을 찾고 있습니다.

## 해결 방법 1: Vite의 환경 변수 사용

Vite는 `.env` 파일을 통해 환경 변수를 설정할 수 있습니다. 이 환경 변수를 `index.html` 파일에 적용할 수 있습니다. 이렇게 하면 CLI 인수를 통해 설정한 값에 따라 `src` 속성을 동적으로 바꿀 수 있습니다.

1. 먼저, 프로젝트 루트에 `.env` 파일을 생성합니다.
2. 이 파일에 `VITE_SCRIPT_SRC=your_script.js`와 같은 형식으로 환경 변수를 설정합니다.
3. `index.html`에서는 `<script src="$VITE_SCRIPT_SRC"></script>`와 같은 방식으로 환경 변수를 사용합니다.

## 해결 방법 2: Vite 플러그인 사용

Vite는 플러그인 시스템을 지원하기 때문에, 이를 이용해 `index.html`의 `src` 속성을 동적으로 바꿀 수 있습니다. 예를 들어, `vite-plugin-html` 플러그인을 사용하면 템플릿 엔진을 통해 동적으로 HTML을 생성할 수 있습니다.

1. `vite-plugin-html`을 설치합니다.
2. `vite.config.js`에서 플러그인을 설정합니다.
3. 이 플러그인의 옵션을 통해 `src` 속성을 동적으로 설정할 수 있습니다.

## 주의 사항: Error `UNKNOWN_OPTION`

이러한 동적 설정을 시도할 때 `UNKNOWN_OPTION` 이라는 에러가 발생할 수 있습니다. 이 에러는 Vite가 인식하지 못하는 옵션을 사용했을 때 나타납니다. 이를 해결하기 위해서는 옵션 이름을 정확히 확인해야 합니다.

## 결론

Vite에서 `index.html`의 `src` 속성을 동적으로 설정하기 위해선 환경 변수를 사용하거나, Vite의 플러그인 시스템을 활용할 수 있습니다. 각 방법은 그 자체로 효과적이며, 프로젝트의 요구 사항에 따라 적절한 방법을 선택하면 됩니다.