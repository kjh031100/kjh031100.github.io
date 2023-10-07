---
title: React Native에서 React Native Gesture Handler로 화면 경계를 기준으로 스와이프 제한하기
date: 2023-07-26 20:00:00 +0900
categories:
  - JavaScript
tags:
  - ReactNative
---

## 문제 상황

React Native 프로젝트에서 화면 스와이프를 구현하려고 할 때, 종종 사용자가 화면 밖으로 너무 멀리 스와이프하는 문제가 발생한다. 이를 해결하기 위해 React Native Gesture Handler를 사용해 볼 수 있다. 이 문서에서는 React Native Gesture Handler를 사용하여 화면 경계를 기준으로 스와이프를 제한하는 방법을 자세하게 알아볼 것이다.

## `translateX`와 `translateY` 속성 이해하기

`translateX`와 `translateY`는 객체가 화면에서 이동할 거리를 설정하는 속성이다. 예를 들어, `translateX: 50`은 객체를 X축 방향으로 50픽셀만큼 이동시킨다. 이 속성을 이해하고 적용하면, 화면 경계에 맞게 객체를 이동시킬 수 있다.

## `onGestureEvent` 이벤트 처리

`onGestureEvent`는 사용자가 화면에 어떤 제스처를 취했는지 감지하는 이벤트 핸들러다. 이를 통해 현재의 `translateX`와 `translateY` 값을 알 수 있고, 그 값을 화면 크기에 맞게 제한할 수 있다.

## 코드 예시: `onGestureEvent` 이벤트를 이용한 스와이프 제한

다음은 React Native Gesture Handler를 사용하여 `onGestureEvent` 이벤트를 이용해 스와이프를 화면 경계에 맞게 제한하는 코드 예시다.

```javascript
import React from 'react';
import { PanGestureHandler, State } from 'react-native-gesture-handler';
import Animated from 'react-native-reanimated';

const App = () => {
  const translateX = new Animated.Value(0);
  const translateY = new Animated.Value(0);

  const onGestureEvent = Animated.event([
    {
      nativeEvent: {
        translationX: translateX,
        translationY: translateY,
      },
    },
  ]);

  return (
    <PanGestureHandler
      onGestureEvent={onGestureEvent}
      onHandlerStateChange={(event) => {
        if (event.nativeEvent.oldState === State.ACTIVE) {
          // 화면 경계 제한 로직
        }
      }}
    >
      <Animated.View
        style={{
          transform: [
            { translateX },
            { translateY },
          ],
        }}
      />
    </PanGestureHandler>
  );
};
```

## 핵심 포인트

- `translateX`와 `translateY` 속성을 사용하여 객체의 이동 거리를 설정한다.
- `onGestureEvent` 이벤트 핸들러를 통해 현재의 `translateX`와 `translateY` 값을 얻는다.
- `onHandlerStateChange` 이벤트를 이용하여 스와이프가 끝났을 때 화면 경계를 기준으로 제한한다.

이러한 방법을 통해 React Native에서 화면 경계를 기준으로 스와이프를 쉽게 제한할 수 있다. 이 방법은 사용자 경험을 높이는 데 매우 효과적이다.