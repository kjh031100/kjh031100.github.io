---
title: GitHub에서 호스팅된 외부 JavaScript 파일 링크 및 실행
date: 2023-06-11 20:00:00 +0900
categories:
  - JavaScript
tags:
  - 자바스크립트파일
---

## 문제 상황

Stack Overflow에 게시된 질문에 따르면, 사용자는 GitHub에서 호스팅되는 외부 JavaScript 파일을 링크하고 실행하는 방법에 대해 논의하고 있습니다. 사용자는 로컬 JavaScript 파일의 연결된 참조를 GitHub 원시 버전으로 변경하려고 했지만, 테스트 파일이 작동하지 않았습니다. 오류 메시지는 다음과 같습니다: “Refused to execute script from … because its MIME type (text/plain) is not executable, and strict MIME type checking is enabled.”

## 해결 방법

이 문제를 해결하기 위한 좋은 방법은 jsdelivr.net을 사용하는 것입니다. 다음은 이를 사용하는 방법입니다:

1. GitHub에서 링크를 찾아 ‘Raw’ 버전으로 이동합니다.
2. URL을 복사합니다.
3. raw.githubusercontent.com을 cdn.jsdelivr.net으로 변경합니다.
4. 사용자 이름 앞에 /gh/를 삽입합니다.
5. 브랜치 이름을 제거합니다.
6. 원하는 버전을 @version으로 삽입합니다(이 작업을 하지 않으면 최신 버전이 제공되며, 이로 인해 파일의 장기 캐싱이 발생할 수 있습니다).

예시:

- 원본 URL: http://raw.githubusercontent.com/<username>/<repo>/<branch>/path/to/file.js
- 최신 버전을 얻기 위한 URL: http://cdn.jsdelivr.net/gh/<username>/<repo>/path/to/file.js
- 특정 버전 또는 커밋 해시를 얻기 위한 URL: http://cdn.jsdelivr.net/gh/<username>/<repo>@<version or hash>/path/to/file.js

## 주의 사항

최신 링크를 사용하면 파일의 장기 캐싱이 발생하여 새로운 버전을 푸시해도 링크가 업데이트되지 않을 수 있습니다. 커밋 해시 또는 태그별로 파일에 링크하면 버전별로 링크가 고유해집니다.

2013년부터 GitHub는 X-Content-Type-Options: nosniff를 사용하기 시작했는데, 이는 더 현대적인 브라우저에게 엄격한 MIME 유형 검사를 강제합니다. 그런 다음 서버에서 반환된 MIME 유형으로 원시 파일을 반환하므로, 브라우저가 파일을 의도대로 사용하는 것을 방지합니다(브라우저가 설정을 준수하는 경우).