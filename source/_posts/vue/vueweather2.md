---
layout: post
title: "Vue + Nuxt 날씨 서비스 만들기 - 2.디자인과 기본 세팅"
date : 2022-10-31
categories: [vue]
tags: [vue]
---

본격적인 코딩전에 디자인을 확인하겠습니다.
피그마로 작업합니다.

### 1.디자인
![flex](/images/post/forecast.jpg)

무료 피그마 템플릿 사이트에 있는 Weather App 템플릿을 참고하였습니다.
참고한 템플릿 주소 : <a href="https://figmaelements.com/weather-app-concept/" target="_blank" rel="noopener noreferrer">https://figmaelements.com/weather-app-concept</a>

### 2.페이지 구성

페이지와 레이아웃은 모두 인트로와 상세 페이지로 구성합니다.
/pages, /layouts

### 3.컴포넌트 구성

![flex](/images/post/forecast2.jpg)

각 섹션별로 컴포넌트로 구성하고 하위 컴포넌트는 코딩을 진행하면서
필요할시에 만들도록 하겠습니다.
/components

### 4.날씨 API

api는 <a href="https://openweathermap.org" target="_target" rel="noopener noreferrer">https://openweathermap.org</a> 의 api를 사용합니다.
분당 호출수가 제한이 있긴 하지만 무료입니다.
현재 날씨와 앞으로의 예보까지 확인할 수 있는 OneCall API를 활용하고,
미세먼지 예보는 Air Pollution를 활용합니다.
추가로 현재 위치 추적을 위해 Geo API도 활용할 수 있습니다.

### 5.비동기 호출

Nuxt 설치시 사용설정을 했던 @nuxt/axios를 사용합니다.
<a href="https://www.npmjs.com/package/@nuxtjs/axios" target="_blank" rel="noopener noreferrer">https://www.npmjs.com/package/@nuxtjs/axios</a>

### 6.Store
store에는 현재 내 위치 기본으로 저장하고,
진행하면서 필요할시에 추가해나갑니다.

### 7.CSS
SCSS를 사용합니다.
컴포넌트 별로 CSS를 선언하지 않고 공통 CSS 한벌을 사용합니다.

기본적인 정의와 세팅은 모두 끝났습니다.
이제 본격적인 코딩을 해보도록 하겠습니다.


