---
title: React Pro Sidebar와 React Router Dom 활성화 서브메뉴 문제 해결법
date: 2023-09-24 20:00:00 +0900
categories:
  - JavaScript
tags:
  - React
  - ProSidebar
  - RouterDom
---

## 문제 상황

`React Pro Sidebar v1.0.0`과 `React Router Dom v6.16.0`을 함께 사용하려고 하지만, 서브메뉴가 활성화되지 않는 문제가 발생했습니다. 특히 이 문제는 `useNavigate`와 `useLocation` 훅을 사용할 때 주로 나타납니다.

## 오류 코드

`Error: Unable to activate submenu`

## 원인 분석

`React Router Dom v6`에서는 `useNavigate`와 `useLocation`이 새롭게 도입되었고, 이러한 변화로 인해 `React Pro Sidebar`의 기존 설정과 충돌이 발생할 수 있습니다. 특히, 라우팅 설정에서 이전 버전과는 다르게 작동하기 때문에 서브메뉴 활성화에 문제가 생깁니다.

## 해결 방안

1. **useNavigate와 useLocation 적용**: 이 훅들을 적절히 활용하여 현재 위치와 이동 경로를 파악합니다.
  
2. **조건문 적용**: 서브메뉴가 활성화되어야 할 조건을 명확히 설정합니다. 예를 들어, 현재 위치가 특정 라우트와 일치하는지 확인합니다.
  
3. **Sidebar 컴포넌트 수정**: 필요하다면 `React Pro Sidebar`의 컴포넌트를 직접 수정하여 라우터와 호환성을 높입니다.

## 예시 코드

```javascript
const navigate = useNavigate();
const location = useLocation();

const isActive = (route) => {
  return location.pathname === route;
};

<ProSidebar>
  <Menu iconShape="square">
    <MenuItem active={isActive('/dashboard')} onClick={() => navigate('/dashboard')}>
      대시보드
    </MenuItem>
    <SubMenu title="설정" active={isActive('/settings')}>
      <MenuItem active={isActive('/settings/profile')} onClick={() => navigate('/settings/profile')}>
        프로필 설정
      </MenuItem>
    </SubMenu>
  </Menu>
</ProSidebar>
```

이렇게 하면 `React Pro Sidebar`와 `React Router Dom v6`을 함께 사용하면서 서브메뉴 활성화 문제를 해결할 수 있습니다.