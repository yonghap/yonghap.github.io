---
layout: post
title: "[고도몰] 새로운 컨트롤러 만들기"
date : 2022-08-24
categories: [solution]
tags: [solution,godomall]
---

내 쇼핑몰/test/test로 접속을 위한 새로운 컨트롤러를 만들어 보겠습니다.


### 1.개발소스 관리 접속

고도몰 관리자에 접속하여 [개발소스 관리]로 접속합니다.

![개발소스관리](/images/post/godomall2.gif)

### 2.원본소스에서 복사

저희가 추가할 주소는 /test/test 입니다.
우선 고도몰 원본 개발 소스에서 해당 컨트롤러를 개발작업 소스로 복사합니다. 
로직은 아래와 같이 진행됩니다.

- [고도몰 원본소스 보기]에서 [개발 작업소스]로 복사
- FTP에 접속하여 해당 소스 편집 
- [개발 작업소스] 목록에서 [운영소스에 적용] 실행

![개발소스복사](/images/post/godomall3.gif)

이미 고도몰 원본소스에 테스트용 컨트롤러가 있습니다.
복사합니다.

![개발소스복사확인](/images/post/godomall4.gif)

복사된 소스를 확인합니다.
[적용하기] 소스를 수정한뒤 적용합니다.

### 3.소스 수정

위에서 복사한 컨트롤러 파일은 FTP내에 있습니다.
/data/module/Controller/Front/Test 
다운로드하여 소스 편집기 파일로 엽니다.

###### TestController.php 

```
<?php
/**
 * This is commercial software, only users who have purchased a valid license
 * and accept to the terms of the License Agreement can install and use this
 * program.
 *
 * Do not edit or add to this file if you wish to upgrade Godomall5 to newer
 * versions in the future.
 *
 * @copyright ⓒ 2016, NHN godo: Corp.
 * @link http://www.godo.co.kr
 */
namespace Controller\Front\Test;

class TestController extends \Bundle\Controller\Front\Test\TestController
{
    public function index() {
	$hello = "Hello World";
	$this->setData('hello',$hello);
    }
  
}
```

컨트롤러 내 index 함수에 변수를 선언해주었습니다.
이제 저 변수는 View 페이지내에서 사용할 수 있습니다.


### 4.View 페이지 생성

View 페이지를 생성할 위치 입니다. 
/data/skin/front/스킨명/test/test.html 
이전글을 참고하면 더 자세한 생성위치를 알 수 있습니다.

###### test.html

```
{=hello}
```

이제 도메인/test/test를 접속하여 확인합니다.