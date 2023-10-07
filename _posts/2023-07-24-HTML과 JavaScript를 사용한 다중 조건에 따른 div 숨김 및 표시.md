---
title: HTML과 JavaScript를 사용한 다중 조건에 따른 div 숨김 및 표시
date: 2023-07-24 20:00:00 +0900
categories:
  - JavaScript
tags:
  - 자바스크립트조건문
---

## 문제 상황: `Multiple condition to show/hide div based on certain radio and select option`

웹 페이지에서 라디오 버튼(radio button)이나 선택 상자(select box)의 상태에 따라 특정 div를 숨기거나 보여주고 싶을 때가 있습니다. StackOverflow에 올라온 질문에서는 이러한 문제에 대한 해결책을 찾고 있습니다. 다중 조건에 따라 어떻게 div를 제어할 수 있는지 알아보겠습니다.

## 조건 분기를 위한 JavaScript 기초

JavaScript는 웹 페이지의 동적인 부분을 제어하는 프로그래밍 언어입니다. 동적이라는 말은 사용자의 조작에 따라 내용이 변하는 것을 의미합니다. 여기서는 JavaScript를 사용해 라디오 버튼이나 선택 상자의 상태에 따라 div를 숨기거나 보여주는 기능을 구현하려고 합니다.

## HTML 구조 설정

먼저 HTML에서 필요한 라디오 버튼과 선택 상자, 그리고 숨기거나 보여줄 div를 만듭니다.

```html
<input type="radio" id="option1" name="choice" value="1">
<label for="option1">옵션 1</label>

<input type="radio" id="option2" name="choice" value="2">
<label for="option2">옵션 2</label>

<select id="mySelect">
  <option value="A">A</option>
  <option value="B">B</option>
</select>

<div id="myDiv">
  내용
</div>
```

## JavaScript로 조건 처리

이제 JavaScript를 이용해 다중 조건에 따라 div를 제어하는 코드를 작성합니다.

```javascript
document.addEventListener('DOMContentLoaded', function() {
  const radioButtons = document.getElementsByName('choice');
  const selectBox = document.getElementById('mySelect');
  const targetDiv = document.getElementById('myDiv');

  function checkConditions() {
    let selectedRadioValue;
    for (let i = 0; i < radioButtons.length; i++) {
      if (radioButtons[i].checked) {
        selectedRadioValue = radioButtons[i].value;
        break;
      }
    }
    const selectedOptionValue = selectBox.value;

    if (selectedRadioValue === '1' && selectedOptionValue === 'A') {
      targetDiv.style.display = 'block';
    } else {
      targetDiv.style.display = 'none';
    }
  }

  selectBox.addEventListener('change', checkConditions);
  for (let i = 0; i < radioButtons.length; i++) {
    radioButtons[i].addEventListener('change', checkConditions);
  }
});
```

이 코드는 두 가지 입력 방식, 즉 라디오 버튼과 선택 상자에 따라 div의 표시 상태를 제어합니다. `checkConditions` 함수는 현재 선택된 라디오 버튼과 선택 상자의 값을 확인한 후, 해당 값에 따라 div를 숨기거나 표시합니다.

이렇게 하면 다중 조건에 따라 div를 제어할 수 있습니다. 이 기술은 사용자의 입력에 따라 동적으로 웹 페이지를 변경할 때 유용하게 사용할 수 있습니다.