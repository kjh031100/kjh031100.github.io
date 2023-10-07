---
title: Access-Control-Allow-Origin 헤더가 요청된 리소스에 없음
date: 2023-06-12 20:00:00 +0900
categories:
  - JavaScript
tags:
  - CORS
---

## 문제 상황

Stack Overflow에 게시된 질문에 따르면, 사용자는 HP Alm의 REST API에서 데이터를 가져오려고 시도할 때 "No ‘Access-Control-Allow-Origin’ header is present on the requested resource"라는 오류 메시지를 받고 있습니다. 사용자는 이 문제가 자신의 로컬호스트에서 데이터를 가져오려고 시도하기 때문에 발생하며, 해결책은 Cross-Origin Resource Sharing (CORS)를 사용하는 것이라고 이해하고 있습니다.

## 해결 방법

이 문제를 해결하는 한 가지 방법은 요청 헤더에 'Access-Control-Allow-Origin’과 'Access-Control-Allow-Credentials’를 추가하는 것입니다. 그러나 이 헤더들은 응답에 속하며, 요청에는 포함되지 않아야 합니다. 따라서 이들을 제거해야 합니다.

또한, 사용자의 요청에 'Content-Type: application/json’이 있으므로 CORS 사전 전송이 트리거되었습니다. 이로 인해 브라우저는 OPTIONS 메서드로 요청을 보냈습니다.

백엔드에서는 이 사전 전송된 요청을 처리하고 다음과 같은 응답 헤더를 반환해야 합니다:

- Access-Control-Allow-Origin : http://localhost:3000
- Access-Control-Allow-Credentials : true
- Access-Control-Allow-Methods : GET, POST, OPTIONS
- Access-Control-Allow-Headers : Origin, Content-Type, Accept

## 주의 사항

Chrome CORS 플러그인을 사용하면 다른 오류 메시지가 발생할 수 있습니다: “The value of the ‘Access-Control-Allow-Origin’ header in the response must not be the wildcard ‘*’ when the request’s credentials mode is ‘include’. Origin ‘http://127.0.0.1:3000’ is therefore not allowed access.” 이 문제를 해결하려면 플러그인이 프론트엔드 JavaScript 코드의 실제 원본을 가짜 ‘Access-Control-Allow-Origin’ 응답 헤더의 값으로 설정하도록 해야 합니다.