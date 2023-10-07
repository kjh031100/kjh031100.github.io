---
title: PHP에서 Headers Already Sent 오류 해결 방법
date: 2023-06-01 20:00:00 +0900
categories:
  - PHP
tags:
  - PHP오류
---

## 오류의 이해와 원인 파악

"Headers Already Sent"이란 PHP에서 웹 서버에게 HTTP 헤더를 전송하려고 할 때 발생하는 오류입니다. 이 오류는 HTTP 헤더 전송 이후에 출력 버퍼(Output Buffer)에 데이터가 존재하는 경우에 발생합니다. 주로, PHP 스크립트 상단에 있는 불필요한 공백, HTML 코드, 또는 `echo`와 `print` 함수로 인해 발생합니다.

## 해결 방법 1: 출력 전에 헤더 전송

첫 번째 해결 방법은 헤더를 전송하기 전에 어떠한 출력도 하지 않는 것입니다. `header()` 함수를 호출하기 전에 `echo`, `print`, HTML 코드 또는 공백이 없어야 합니다.

```php
<?php
header('Location: http://example.com');
// 출력하지 않고 헤더를 전송
exit();
```

## 해결 방법 2: 출력 버퍼 사용

두 번째 방법은 출력 버퍼를 사용하는 것입니다. `ob_start()`와 `ob_end_flush()` 함수를 사용하면 출력 버퍼링을 활성화할 수 있습니다. 이렇게 하면 `header()` 함수를 호출하기 전의 출력이 버퍼에 저장됩니다.

```php
<?php
ob_start();
echo "Hello, World!";
header('Location: http://example.com');
ob_end_flush();
```

## 해결 방법 3: UTF-8 BOM 제거

세 번째 방법은 UTF-8 BOM(Byte Order Mark)를 제거하는 것입니다. 텍스트 에디터에서 UTF-8 BOM이 없는 형식으로 파일을 저장하세요. 대표적인 텍스트 에디터인 Notepad++에서는 "Encoding" 메뉴에서 "UTF-8 without BOM"을 선택할 수 있습니다.

## 주의사항: `exit()` 또는 `die()` 사용

`header()` 함수 호출 후에는 `exit()` 또는 `die()` 함수를 사용하여 스크립트 실행을 중단하세요. 이렇게 하면 추가적인 오류나 문제를 방지할 수 있습니다.

```php
<?php
header('Location: http://example.com');
exit();
```

이러한 방법들을 통해 "Headers Already Sent" 오류를 효과적으로 해결할 수 있습니다. 각 방법의 적용은 상황에 따라 다르므로 문제의 원인을 정확히 파악한 후 적절한 해결 방법을 선택하는 것이 중요합니다.