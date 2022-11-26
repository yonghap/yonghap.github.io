---
layout: post
title: "[고도몰] 쇼핑몰 커스터마이징 세팅"
date : 2022-08-23
categories: [solution]
tags: [solution,godomall]
---

고도몰 커스터마이징을 위한 기본 세팅입니다.
아래 개발 가이드를 참고합니다.
<a href="http://doc.godomall5.godomall.com/Getting_Started/Architecture" target="_blank">고도몰 개발 가이드</a>
<a href="http://doc.godomall5.godomall.com/godo/coding/index.html" target="_blank">고도몰 코딩 컨벤션</a>

고도몰5 Pro는 MVC(Model, View, Controller) 패턴으로 만들어져 있습니다. 
Model는 데이터베이스 연동 
View는 화면의 출력 담당, 
Controller는 Model과 View의 동작 및 연결을 담당합니다.


### 기본 개념

들어가기 전에 고도몰 개발 가이드에서 아래 개념을 숙지해 둡니다.

![1](/images/post/godomall1.gif)

#### Controller 만들기

```
// Controller 파일 생성
/front/폴더명/파일명Controller.php
```

#### View 만들기

View 페이지도 만들어 줍니다.

```
// View 파일 생성
/user/data/skin/front/스킨명/폴더명/파일명.html
```

View 파일이 없으면 컨트롤러 오류가 납니다. 
http://example.com/폴더명/파일명 으로 접속하여 확인합니다.

- 컨트롤러 생성과 작성 (기존 컨트롤러 수정일 경우 상속)
- View 작성
- 동작 확인

새로운 컨트롤러의 추가나 기존 컨트롤러의 수정이나 모두 로직은 비슷합니다.
고도몰 개발 가이드에 Controller, DB, Routing, Security까지 잘 나와 있으니 꼭 참고합니다.