---
title: Xcode에서 PhoneGap 앱의 JavaScript 오류 확인하기
date: 2023-06-16 20:00:00 +0900
categories:
  - JavaScript
tags:
  - PhoneGap오류
---

## 문제 상황

Xcode에서 PhoneGap 앱의 JavaScript 오류를 확인하려고 합니다. 근데 Xcode의 콘솔이 JavaScript 오류를 표시하지 않습니다.

## 해결 방법

PhoneGap 앱에서 JavaScript 오류를 보고 디버깅하는 가장 좋은방법은 Safari 브라우저의 웹 인스펙터를 iOS 앱의 웹 뷰에 연결하는 것입니다. 하지만 이 방법을 사용하려면 최소한 iOS 6가 필요합니다. 다음은 이를 사용하는 방법입니다:

1. iPad 또는 iPhone에서 설정 앱을 사용하여 Safari의 고급 설정에서 웹 인스펙터를 활성화합니다.
2. 장치를 Mac에 USB로 연결합니다(그러면 Safari의 개발 메뉴에 표시됩니다).
3. 앱을 시작합니다.
4. 디버깅하려는 웹 뷰로 이동합니다.
5. Mac에서 Safari 개발 메뉴를 선택하고, 서브 메뉴에서 장치 이름과 앱(HTML 페이지)을 선택합니다.
6. 웹 인스펙터 창이 열리고, DOM을 탐색하고, 브레이크포인트를 설정하는 등의 작업을 할 수 있게 됩니다.

## 주의 사항

Safari 웹 인스펙터를 사용하여 원격 디버깅을 하는 것은 iOS 시뮬레이터와 함께 작동하며, 각 iOS 버전에 대해 특정 최소 버전의 데스크톱 Safari가 필요합니다. 예를 들어, iOS 6는 Safari 6 이상, iOS 7은 Safari 6.1 이상, iOS 8은 Safari 7.1 이상, iOS 9는 Safari 8 이상, iOS 10은 Safari 9/10 이상, iOS 11은 Safari 11 이상, 그리고 iOS 12는 Safari 12 이상이 필요합니다.