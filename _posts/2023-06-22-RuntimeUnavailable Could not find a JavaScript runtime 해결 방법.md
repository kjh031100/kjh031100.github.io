---
title: ExecJS 오류 JavaScript 런타임을 찾을 수 없음 해결 방법
date: 2023-06-22 20:00:00 +0900
categories:
  - JavaScript
tags:
  - 자바스크립트런타임
---

## 오류 개요

StackOverflow에서 자주 발생하는 문제 중 하나는 'ExecJS::RuntimeUnavailable: Could not find a JavaScript runtime'이라는 오류입니다. 이 오류는 특히 Ruby on Rails와 같은 웹 프레임워크에서 JavaScript 코드를 실행하려고 할 때 나타나곤 합니다.

## 원인 파악

이 오류는 시스템에 적절한 JavaScript 런타임이 설치되지 않았을 때 발생합니다. JavaScript 런타임은 JavaScript 코드를 실행할 수 있는 환경을 의미합니다. 예를 들어, Node.js나 Google V8 같은 것이 이에 해당합니다.

## 해결 방법 1: Node.js 설치

가장 간단한 해결책은 Node.js를 설치하는 것입니다. Node.js는 서버 측에서 실행되는 JavaScript 런타임입니다. 이를 통해 여러분의 시스템에 JavaScript 코드를 실행할 수 있는 환경을 제공합니다.

1. **Linux 사용자**: 터미널을 열고 다음 명령어를 입력합니다.
    ```
    sudo apt update
    sudo apt install nodejs
    ```
2. **Mac 사용자**: Homebrew를 이용하여 다음과 같이 설치합니다.
    ```
    brew update
    brew install node
    ```
3. **Windows 사용자**: Node.js 공식 홈페이지에서 인스톨러를 다운로드하여 설치합니다.

## 해결 방법 2: 환경 변수 설정

시스템에 이미 Node.js나 다른 JavaScript 런타임이 설치되어 있지만 여전히 문제가 발생한다면, 환경 변수가 제대로 설정되지 않은 것일 수 있습니다.

1. **PATH 변수 확인**: 터미널에 `echo $PATH`를 입력하여 PATH 변수에 JavaScript 런타임의 경로가 포함되어 있는지 확인합니다.
2. **환경 변수 추가**: 적절한 경로를 PATH 변수에 추가합니다.

## 해결 방법 3: Gemfile 수정

Ruby on Rails 프로젝트에서 이 문제가 발생한다면, `Gemfile`에 JavaScript 런타임을 명시적으로 추가할 수 있습니다.

```ruby
gem 'execjs'
gem 'therubyracer', platforms: :ruby
```

이후 `bundle install` 명령어를 실행하여 변경사항을 적용합니다.

## 마치며

'ExecJS::RuntimeUnavailable: Could not find a JavaScript runtime' 오류는 다양한 원인으로 발생할 수 있지만, 대부분의 경우 위의 방법 중 하나로 해결이 가능합니다. 이 글을 통해 문제를 빠르게 해결하고 원활한 개발 활동을 이어가시길 바랍니다.