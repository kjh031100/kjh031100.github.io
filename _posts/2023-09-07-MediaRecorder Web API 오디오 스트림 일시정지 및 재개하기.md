---
title: MediaRecorder Web API 오디오 스트림 일시정지 및 재개하기
date: 2023-09-07 20:00:00 +0900
categories:
  - JavaScript
tags:
  - MediaRecorder
  - WebAPI
---

## 오디오 스트림이란 무엇인가?

오디오 스트림이란 연속된 오디오 데이터의 흐름을 의미합니다. 이러한 스트림은 인터넷을 통해 실시간으로 오디오 데이터를 전송할 때 자주 사용됩니다. 예를 들어, 라이브 방송, 웹 회의, 또는 스트리밍 서비스에서 이 기술이 활용됩니다.

## MediaRecorder Web API 소개

MediaRecorder Web API는 웹에서 멀티미디어 데이터, 특히 오디오와 비디오를 녹화하는 데 사용됩니다. 이 API를 사용하면 브라우저에서 직접 미디어 녹화가 가능하며, 추가적인 플러그인이나 외부 라이브러리가 필요 없습니다.

## `pause()`와 `resume()` 메서드

MediaRecorder의 `pause()` 메서드는 현재 녹화 중인 미디어 스트림을 일시정지합니다. 반대로, `resume()` 메서드는 일시정지된 녹화를 다시 시작합니다. 이 두 메서드는 오디오 스트림 뿐만 아니라 비디오 스트림에도 동일하게 적용됩니다.

```javascript
const mediaRecorder = new MediaRecorder(stream);

// 녹화 시작
mediaRecorder.start();

// 녹화 일시정지
mediaRecorder.pause();

// 녹화 재개
mediaRecorder.resume();
```

## 오류 처리: `InvalidStateError`

예외 상황을 처리할 때 자주 발생하는 오류 중 하나는 `InvalidStateError`입니다. 이 오류는 일반적으로 MediaRecorder 객체의 현재 상태와 메서드 호출이 일치하지 않을 때 발생합니다. 예를 들어, 녹화가 시작되지 않은 상태에서 `pause()` 메서드를 호출하면 이러한 오류가 발생할 수 있습니다.

## 결론

MediaRecorder Web API를 사용하여 웹에서 오디오 또는 비디오 스트림을 녹화하고, `pause()`와 `resume()` 메서드로 녹화를 일시정지하거나 재개할 수 있습니다. 하지만 사용 중 예외 상황을 잘 처리해야 하며, 특히 `InvalidStateError`와 같은 오류에 주의해야 합니다. 이를 통해 더 안정적인 미디어 녹화 애플리케이션을 개발할 수 있습니다.