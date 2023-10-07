---
title: MediaRecorder Web API 오디오 스트림(마이크) 일시정지 및 재개방법
date: 2023-07-28 20:00:00 +0900
categories:
  - JavaScript
tags:
  - MediaRecorder
---

## 오류 이름: No specific error mentioned in the original text

## 들어가기 전에: MediaRecorder Web API란 무엇인가?

MediaRecorder Web API는 웹에서 오디오 또는 비디오를 녹음할 수 있도록 도와주는 기능입니다. 이 API를 이용하면 웹 사이트나 앱에서 사용자의 마이크나 카메라에 접근해 미디어를 녹음하거나 저장할 수 있습니다. 

## MediaRecorder의 기본 사용법

MediaRecorder는 기본적으로 `start()`, `stop()`, `pause()` 및 `resume()` 등의 메서드를 제공합니다. 

- `start()`: 녹음을 시작합니다.
- `stop()`: 녹음을 중지하고 데이터를 반환합니다.
- `pause()`: 녹음을 일시정지합니다.
- `resume()`: 일시정지된 녹음을 다시 시작합니다.

## MediaRecorder로 마이크 일시정지 및 재개하기

일반적으로 MediaRecorder API를 사용하여 마이크 녹음을 일시정지하고 재개하는 작업은 아래와 같습니다.

1. MediaRecorder 객체를 생성하고 초기화합니다.
2. `pause()` 메서드를 호출하여 녹음을 일시정지합니다.
3. `resume()` 메서드를 호출하여 녹음을 다시 시작합니다.

### 예제 코드

```javascript
// MediaStream 객체 가져오기 (이 경우에는 마이크)
navigator.mediaDevices.getUserMedia({ audio: true })
  .then(stream => {
    const mediaRecorder = new MediaRecorder(stream);

    mediaRecorder.start();

    // 일시정지 버튼을 눌렀을 때
    document.querySelector("#pauseButton").addEventListener("click", () => {
      mediaRecorder.pause();
    });

    // 재개 버튼을 눌렀을 때
    document.querySelector("#resumeButton").addEventListener("click", () => {
      mediaRecorder.resume();
    });
  });
```

## 주의할 점

- 녹음을 일시정지한 후에도 MediaStream은 계속 실행됩니다. 이것은 녹음이 일시정지되었더라도 마이크가 완전히 중지되지 않는다는 것을 의미합니다.
  
## 마치며

MediaRecorder Web API는 오디오 또는 비디오 녹음을 쉽게 해주는 도구입니다. 특히, 마이크를 일시정지하고 재개하는 기능을 제공하므로 다양한 미디어 관련 웹 애플리케이션에서 유용하게 사용할 수 있습니다. 이 기능을 올바르게 활용하면 사용자 경험을 크게 향상시킬 수 있습니다.