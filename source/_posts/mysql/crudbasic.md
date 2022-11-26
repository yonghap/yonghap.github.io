---
layout: post
title: "SELECT, INSERT, UPDATE, DELETE 문법 정리"
date : 2022-09-22
categories: [mysql]
tags: [mysql]
---

백엔드 개발자가 아니라 MySql 사용할때마다 헷갈리는 부분이 있어,
가장 기본적으로 사용하는 SELECT, INSERT, UPDATE, DELETE 문법을 정리해보려고 합니다.

### 1.SELECT
##### 1) 모든 데이터 조회
```
SELECT * FROM 테이블명;
```
##### 2) 해당 필드명 조회
```
SELECT 필드명1, 필드명2 FROM 테이블명;
```
##### 3) 조건부(WHERE) 조회
```
SELECT * FROM 테이블명 WHERE 조건식;
SELECT * FROM user WHERE user_no = 1;
SELECT * FROM user WHERE user_no >= 5;
SELECT user_no FROM user WHERE user_no = 1;
```
##### 4) 정렬(ORDER BY) 조회
ASC(오름차순)이 기본값이며 선언하지 않을시 적용됩니다.
숫자를 적을경우 칼럼 번호로 정렬됩니다.
```
SELECT * FROM 테이블명 WHERE 조건식 ORDER BY 정렬기준필드 DESC;
SELECT * FROM 테이블명 WHERE 조건식 ORDER BY 정렬기준필드 ASC;
SELECT * FROM user WHERE user_no >= 5 ORDER BY user_no DESC;
SELECT * FROM user WHERE user_no >= 5 ORDER BY user_no DESC, name DESC;
SELECT * FROM user WHERE user_no >= 5 ORDER BY 1 DESC;
```

##### 5) 문자열(like) 조회
###### 일부라도 포함이면 조회
```
SELECT * FROM user_name WHERE user_name LIKE "%park%";
```
###### 앞이나 뒤문자 상관없이 조회
```
SELECT * FROM user_name WHERE user_name LIKE "%park";
SELECT * FROM user_name WHERE user_name LIKE "park%";
```
###### 문자 없을때 조회
```
SELECT * FROM user_name WHERE NOT user_name="park";
```
###### 여러개의 조건 조회
```
SELECT * FROM user_name WHERE user_no LIKE "%5%" AND user_name LIKE "%park%";
```
###### 여러개의 검색어 조회
```
SELECT * FROM user_name WHERE user_name LIKE "%park%lee%";
```


### 2.INSERT
```
INSERT INTO 테이블이름 (필드명1,필드명2...) VALUES (값1,값2...)
INSERT INTO 테이블이름 VALUES (값1,값2...)
INSERT INTO user (id,name) VALUES ('1','park');
INSERT INTO user VALUES ('1','park');
```

### 3.UPDATE
```
UPDATE 테이블이름 SET 필드이름1 = 필드값1, 필드이름2 = 필드값2;
UPDATE 테이블이름 SET 필드이름 = 필드값 WHERE 조건식;
UPDATE user SET user_name = 'park';
UPDATE user SET user_name = 'park' WHERE user_no = 1;
```

### 4.DELETE
```
DELETE FROM 테이블이름;
DELETE FROM 테이블이름 WHERE 조건식;
DELETE FROM user;
DELETE FROM user WHERE user_no = 1;
```

### 5.CREATE
##### 1) 데이터베이스 생성
```
CREATE DATABASE 데이터베이스이름;
CREATE DATABASE user;
```
##### 2) 데이터베이스 선택
```
USE 데이터베이스이름;
USE user;
```
##### 3) 테이블 생성
```
CREATE TABLE 테이블이름 (필드이름1 필드타입1, 필드이름2 필드타입2...);
CREATE TABLE user (
	user_no INT NOT NULL,
	user_name VARCHAR(30),
	user_email VARCHAR(50)
)
```

### 6.기타 SQL
##### 1) AUTO INCREMENT 초기화
```
ALTER TABLE 테이블이름 AUTO_INCREMENT=시작할 값;
ALTER TABLE user AUTO_INCREMENT=1;
```