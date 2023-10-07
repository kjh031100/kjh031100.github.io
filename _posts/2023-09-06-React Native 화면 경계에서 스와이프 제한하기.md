---
title: React Native 화면 경계에서 스와이프 제한하기
date: 2023-09-06 20:00:00 +0900
categories:
  - JavaScript
tags:
  - ReactNative
  - 스와이프제한
---

## React Native Gesture Handler를 이용한 해결 방법

React Native에서는 여러 가지 방법으로 사용자의 터치 및 제스처를 관리할 수 있습니다. 그 중에서도 `React Native Gesture Handler`라는 라이브러리가 널리 사용됩니다. 이 라이브러리를 이용하면 터치, 탭, 스와이프 등 다양한 제스처를 쉽게 구현할 수 있습니다.

### PanGestureHandler를 활용한 스와이프 제한

`PanGestureHandler`는 `React Native Gesture Handler`에서 제공하는 컴포넌트 중 하나로, 드래그와 관련된 제스처를 관리합니다. 이를 이용해 화면 경계에서 스와이프를 제한하려면, `onGestureEvent` 속성에서 제스처의 상태와 위치를 모니터링할 수 있습니다.

예를 들어, 스와이프가 화면의 왼쪽 또는 오른쪽 경계를 벗어나면 이동을 제한하도록 코드를 작성할 수 있습니다.

```jsx
import { PanGestureHandler, State } from 'react-native-gesture-handler';

<PanGestureHandler
  onGestureEvent={({ nativeEvent }) => {
    if (nativeEvent.x < 0 || nativeEvent.x > SCREEN_WIDTH) {
      // 화면을 벗어난 경우
      return;
    }
    // 다른 로직 처리
  }}
  onHandlerStateChange={({ nativeEvent }) => {
    if (nativeEvent.oldState === State.ACTIVE) {
      // 제스처가 끝난 후 로직
    }
  }}
>
  {/* 자식 컴포넌트 */}
</PanGestureHandler>
```

### SCREEN_WIDTH와 nativeEvent.x의 이해

- `SCREEN_WIDTH`: 화면의 너비입니다. 이 값을 알아내기 위해서는 React Native의 `Dimensions` API를 사용할 수 있습니다.
- `nativeEvent.x`: 현재 터치되고 있는 화면의 x 좌표입니다. 이 값이 0보다 작거나 `SCREEN_WIDTH`보다 크면 화면을 벗어난 것으로 간주합니다.

이러한 방법으로 `PanGestureHandler`를 적용하면 화면 경계에서의 스와이프를 효과적으로 제한할 수 있습니다. 이 정보가 당신의 문제 해결에 도움이 되길 바랍니다.