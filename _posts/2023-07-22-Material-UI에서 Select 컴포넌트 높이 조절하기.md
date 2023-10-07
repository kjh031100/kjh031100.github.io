---
title: Material-UI에서 Select 컴포넌트 높이 조절하기
date: 2023-07-22 20:00:00 +0900
categories:
  - JavaScript
tags:
  - Material-UI
---

## 문제 상황: Material-UI Select 컴포넌트의 높이 변경이 필요함

React와 Material-UI를 사용하여 앱을 개발하다 보면, 디자인 요구 사항에 맞게 Select 컴포넌트의 높이를 조절해야 할 수 있습니다. 이 경우, Material-UI는 자체적인 스타일링 시스템을 가지고 있기 때문에 일반적인 CSS 방식으로 높이를 변경하기가 어렵습니다.

## 해결 방법 1: `style` 속성을 이용한 높이 조절

Material-UI의 Select 컴포넌트에는 `style` 속성을 사용하여 직접 높이를 설정할 수 있습니다. 이는 가장 간단하고 직관적인 방법으로, 아래와 같이 작성하면 됩니다.

```jsx
<Select
  value={value}
  onChange={handleChange}
  style={{ height: '50px' }}
>
  <MenuItem value={10}>Ten</MenuItem>
  <MenuItem value={20}>Twenty</MenuItem>
  <MenuItem value={30}>Thirty</MenuItem>
</Select>
```

## 해결 방법 2: `makeStyles` 함수와 클래스 지정

Material-UI는 자체적인 스타일링 방식을 제공하는데, `makeStyles` 함수를 이용해서 스타일을 생성하고, 이를 클래스로 적용할 수 있습니다. 이 방식은 좀 더 복잡한 스타일링이 필요할 때 유용합니다.

```jsx
import { makeStyles } from '@material-ui/core/styles';

const useStyles = makeStyles({
  customHeight: {
    height: '50px'
  }
});

const MySelectComponent = () => {
  const classes = useStyles();

  return (
    <Select
      value={value}
      onChange={handleChange}
      className={classes.customHeight}
    >
      // 메뉴 아이템들
    </Select>
  );
};
```

## 에러와 해결책: `Cannot read property 'style' of null`

Material-UI의 Select 컴포넌트에 높이를 설정하는 과정에서 "Cannot read property 'style' of null" 이라는 에러가 발생할 수 있습니다. 이는 대체로 스타일을 적용할 대상 DOM 요소가 아직 생성되지 않았을 때 발생하는 문제입니다. 이 경우, 조건부 렌더링을 통해 해당 DOM 요소가 확실히 존재할 때만 스타일을 적용하는 것이 좋습니다.

## 요약: 높이 조절 방법에 따라 선택하면 효율적

Material-UI의 Select 컴포넌트 높이를 조절하는 방법은 크게 두 가지입니다. 간단한 경우에는 `style` 속성을 사용하고, 복잡한 스타일링이 필요할 때는 `makeStyles` 함수와 클래스를 활용합니다. 에러가 발생할 경우, 대상 DOM 요소가 존재하는지 확인해야 합니다.