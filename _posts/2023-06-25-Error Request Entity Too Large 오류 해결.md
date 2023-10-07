---
title: 해결 방법 Error Request Entity Too Large 오류
date: 2023-06-25 20:00:00 +0900
categories:
  - JavaScript
tags:
  - 자바스크립트오류
---

## 오류 소개

"Error: Request Entity Too Large"는 웹 서버가 클라이언트로부터 너무 큰 데이터를 받았을 때 발생하는 오류입니다. 이 오류는 주로 파일 업로드, 폼 제출 등에서 발생하며, 서버 설정을 수정하여 해결할 수 있습니다.

## 원인 분석

이 오류는 웹 서버가 설정된 요청 크기 제한을 초과하는 데이터를 받을 때 발생합니다. 예를 들어, 웹 서버가 1MB 크기의 데이터만 허용하는데, 2MB 크기의 파일을 업로드하려고 하면 이 오류가 발생합니다.

## 해결 방법: Nginx 서버

1. `nginx.conf` 파일을 열어 `http` 블록 안에 `client_max_body_size` 값을 변경합니다.
   ```nginx
   http {
     client_max_body_size 50M;
   }
   ```
2. Nginx 서버를 재시작합니다.
   ```
   sudo systemctl restart nginx
   ```

## 해결 방법: Apache 서버

1. `.htaccess` 파일을 열거나 생성합니다.
2. 아래의 코드를 추가하여 제한 크기를 변경합니다.
   ```apache
   LimitRequestBody 52428800
   ```

## 해결 방법: Node.js 서버

1. `express` 라이브러리를 사용하는 경우, `body-parser` 미들웨어의 설정을 변경합니다.
   ```javascript
   app.use(bodyParser.json({limit: '50mb'}));
   app.use(bodyParser.urlencoded({limit: '50mb', extended: true}));
   ```

## 주의 사항

값을 너무 크게 설정하면 서버에 부담을 줄 수 있으니, 적절한 크기로 설정해야 합니다.

## 결론

"Error: Request Entity Too Large" 오류는 서버 설정을 적절히 조정하여 해결할 수 있습니다. 필요한 크기와 서버의 용량을 고려하여 설정을 변경하면, 이 오류를 효과적으로 해결할 수 있습니다.