---
layout: post
title: "REST API 정리"
date : 2022-09-23
categories: [mysql]
tags: [mysql]
---

### 1.REST API?
Representational State Transfer
자원을 URI로 표시하고 해당 자원의 상태를 주고 받는 것을 의미

### 2.구성
- **자원** : URI(member/1)
- **행위** : Method (GET,POST,PUT,DELETE)
- **표현** : JSON,XML,TEXT 등


### 3.규칙
- URI는 정보의 자원을 표시해야 한다.(소문자, 명사 사용)
- URI에 행위(Method)가 들어가서는 안된다.
- URI에 동사 행위 표현이 들어가서는 안된다.
- URI에 '/' 구분자는 계층 관계를 나타내는데 사용한다.
- URI에 확장자와 하이픈(-)은 사용하지 않는다.

### 4.Method 사용규칙
- POST : (create) 리소스의 생성
- GET : (Read) 리소스의 조회
- PUT : (Update,Replace) 리소스의 수정
- DELETE : (Delete) 리소스의 삭제

### 5.Methos Sample
#### POST
- **POST** http://www.example.com/customers (신규 고객 추가)
- **POST** http://www.example.com/customers/12345/orders (신규 주문 추가)

#### GET
- **GET** http://www.example.com/customers/12345 (고객 조회)
- **GET** http://www.example.com/customers/12345/orders (고객 주문 조회)
- **GET** http://www.example.com/buckets/sample (버킷 리스트 조회)


#### PUT
- **PUT** http://www.example.com/customers/12345 (고객 정보 수정)
- **PUT** http://www.example.com/customers/12345/orders/98765 (고객 주문 수정)
- **PUT** http://www.example.com/buckets/secret_stuff (버킷 리스트 수정)

#### DELETE
- **DELETE** http://www.example.com/customers/12345 (고객 삭제)
- **DELETE** http://www.example.com/customers/12345/orders (고객 주문 삭제)
- **DELETE** http://www.example.com/bucket/sample (버킷 리스트  삭제)

#### 기타예제
- **GET** /members/show/1 (X) 동사 행위 금지
- **GET** /members/1 (O)
- **GET** /members/insert/2 (X) 동사 행위 금지, 잘못된 메소드 사용
- **POST** /members/2 (O)
- **POST** /posts/put/:id (X)
- **POST** /posts/update/:id (X)
- **PUT** /posts/:id (O) 글 수정시 POST 사용


### 6.상태응답
- **성공** : 200(정상),201(리소스 요청)\
- **실패** : 400(요청 부적절), 401(인증 실패), 403(요청 실패), 500(서버 오류)