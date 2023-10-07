---
title: NPM의 Dependencies, DevDependencies, PeerDependencies 차이점
date: 2023-06-19 20:00:00 +0900
categories:
  - NPM
tags:
  - Dependencies
---

## 개요

NPM(Node Package Manager)을 사용하면서 `package.json` 파일에 나타나는 `dependencies`, `devDependencies`, `peerDependencies` 키워드를 본 적이 있을 것입니다. 이 세 가지 키워드는 패키지를 설치하거나 프로젝트를 관리할 때 중요한 역할을 합니다. 이 글에서는 이들 각각의 차이점과 사용 시기에 대해 자세히 설명하겠습니다.

## Dependencies 란?

`Dependencies`는 애플리케이션을 실행하기 위해 필요한 패키지나 라이브러리를 나타냅니다. 예를 들어, 웹 서버를 만드는 데 필요한 `express`나 데이터베이스를 다루는 `mongoose`와 같은 패키지가 이에 해당합니다. `npm install` 명령어를 실행하면 `dependencies`에 명시된 패키지가 설치됩니다.

```json
{
  "dependencies": {
    "express": "^4.17.1",
    "mongoose": "^5.12.3"
  }
}
```

## DevDependencies 란?

`DevDependencies`는 개발 과정이나 테스트를 위해 필요한 패키지를 나타냅니다. 이 패키지들은 실제 애플리케이션에는 포함되지 않습니다. 예를 들어, 코드 포맷팅 도구인 `prettier`나 테스트 라이브러리인 `jest`가 여기에 해당됩니다. `npm install --save-dev` 명령어로 설치할 수 있습니다.

```json
{
  "devDependencies": {
    "prettier": "^2.3.2",
    "jest": "^27.0.4"
  }
}
```

## PeerDependencies 란?

`PeerDependencies`는 호환성을 위해 필요한 패키지를 나타냅니다. 이 패키지는 사용자가 직접 설치해야 합니다. 예를 들어, `React` 라이브러리를 사용하는 플러그인이 `React` 버전과 호환성을 유지해야 할 때 `peerDependencies`를 사용합니다.

```json
{
  "peerDependencies": {
    "react": "^17.0.0"
  }
}
```

## 정리

- `Dependencies`: 애플리케이션 실행에 필요한 패키지
- `DevDependencies`: 개발과 테스트에 필요한 패키지
- `PeerDependencies`: 호환성을 위해 사용자가 설치해야 하는 패키지

이 세 가지는 각기 다른 목적과 사용 시기가 있으므로, 올바른 카테고리에 패키지를 배치하는 것이 중요합니다.