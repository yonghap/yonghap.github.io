---
layout: post
title: "[고도몰] 관리자 메뉴 추가하기 1"
date : 2022-09-14
categories: [solution]
tags: [solution,godomall]
---

고도몰 관리자의 메뉴를 추가해보겠습니다. 
배너 등록 메뉴처럼 텍스트를 등록하고 어느 페이지에서든 치환코드를 통해 이 텍스트에 접근할 수 있는 기능을 추가하겠습니다. 
해당 메뉴의 이름은 [텍스트 등록]이며 고도몰 관리자의 [디자인] 하위의 [디자인 설정] 하위의 3뎁스에 위치 시키겠습니다.


###### 추가할 메뉴 위치

![admin추가](/images/post/godomall7.gif)


### 1.DB에 3뎁스 메뉴 추가하기

#### 1) 2뎁스의 번호 확인

메뉴를 추가하기 위해서는 Phpmyadmin에서 메뉴를 추가해야 합니다.
2뎁스 메뉴인 [디자인 설정]의 메뉴 번호를 확인합니다.

```
Select adminMenuNo From `es_adminMenu` Where adminMenuDepth = 2 And adminMenuType = 'd' And adminMenuName = '디자인 설정'
```
```
godo00217
```

[디자인 설정]의 관리자 메뉴 고유번호는 godo00217입니다.

#### 2) 3뎁스의 마지막 메뉴번호 확인

[디자인 설정] 하위 메뉴 중 마지막 메뉴의 정렬 번호를 확인합니다.

```
Select max(adminMenuSort) From `es_adminMenu` Where adminMenuDepth = 3 And adminMenuType = 'd' And adminMenuParentNo = 'godo00217'
```

```
920
```

920은 마지막 메뉴의 번호입니다.

![admin추가](/images/post/godomall8.gif)

위 이미지처럼 모든 메뉴는 순서로 되어 있습니다.
마지막 번호가 920이므로 입력될 메뉴의 번호는 1000입니다.

```
Insert Into `es_adminMenu` (adminMenuNo, adminMenuType, adminMenuProductCode, adminMenuPlusCode, 
adminMenuCode, adminMenuDepth, adminMenuParentNo, adminMenuSort, adminMenuName,
adminMenuUrl, adminMenuDisplayType, adminMenuDisplayNo, adminMenuSettingType, adminMenuEcKind, regDt) 
Values ('prefix00001', 'd', 'godomall', null, 
'textList', '3', 'godo00217', '1000', '텍스트 관리',
null, 'y', null, 'd', 'p', now());
```

DB에 메뉴를 삽입합니다 
adminMenuNo는 고유 접두사와 함께 숫자를 붙여줍니다. 
기존의 DB에 삽입된 'godo' 접두사를 사용하면 오류가 발생할 수 있습니다. ('godo숫자 형태의 접두사 사용금지') 
메뉴 정렬 번호와 표시될 텍스트도 추가해 줍니다.
아래처럼 관리자에 메뉴가 추가된걸 확인할 수 있습니다.

![admin추가](/images/post/godomall9.gif)


### 2.관리자 페이지 퍼블리싱

위에서 입력한 메뉴 코드(adminMenuCode) 'textList' 입니다. 
뷰페이지에서는 text_list.php 파일로 생성되어야 합니다. 
FTP내 해당 파일이 삽입 될 경로는 아래와 같습니다. 
[/admin/design/text_list.php] 
여기에 다른 페이지를 참고하여 퍼블리싱을 진행합니다. 
완성된 소스와 화면은 아래와 같습니다.

###### text_list.php

```
<div class="page-header js-affix affix-top" style="width: auto;">
	<h3>텍스트 관리</h3>
</div>
<div class="text-add">
	<div class="table-title gd-help-manual">
		텍스트 등록
	</div>
	<form id="frmSearch" name="" method="get" action="">
		<input type="hidden" name="detailSearch" value="">
		<input type="hidden" name="skinType" value="">
		<table class="table table-cols">
			<colgroup>
				<col class="width-sm">
				<col>
			</colgroup>
			<tbody>
			<tr>
				<th>영역이름</th>
				<td class="form-inline">
					<input type="text" name="keyword" value="" class="form-control" placeholder="영역이름을 입력해 주세요."
					       style="width:100%">
				</td>
			</tr>
			<tr>
				<th>텍스트</th>
				<td class="form-inline">
					<input type="text" name="keyword" value="" class="form-control" placeholder="텍스트를 입력해 주세요.(br포함)"
					       style="width:100%">
				</td>
			</tr>
			</tbody>
		</table>
		<div class="table-btn">
			<input type="submit" value="검색" class="btn btn-lg btn-black">
		</div>
	</form>
</div>
<div class="text-list">
	<div class="table-title gd-help-manual">
		텍스트 목록
	</div>
	<form id="frmList" name="frmList" action="" method="post">
		<table class="table table-rows table-fixed">
			<colgroup>
				<col class="width3p">
				<col class="width10p">
				<col class="width15p">
				<col class="width45p">
				<col class="width12p">
				<col class="width5p">
				<col class="width5p">
			</colgroup>
			<thead>
			<tr>
				<th><input class="js-checkall" type="checkbox" data-target-name="sno"></th>
				<th>번호</th>
				<th>이름</th>
				<th>텍스트</th>
				<th>치환코드</th>
				<th>수정</th>
				<th>삭제</th>
			</tr>
			</thead>
			<tbody class="text-center">
			<tr>
				<td>
					<input name="sno[]" type="checkbox" value="8">
				</td>
				<td>1</td>
				<td>메인상단</td>
				<td>Hello World!  Good Morning!</td>
				<td>[치환코드]</td>
				<td>
					<a href="./banner_register.php?sno=8" class="btn btn-white btn-sm" role="button">수정</a>
				</td>
				<td>
					<a href="./banner_register.php?sno=8" class="btn btn-white btn-sm" role="button">삭제</a>
				</td>
			</tr>
			<tr>
				<td>
					<input name="sno[]" type="checkbox" value="8">
				</td>
				<td>1</td>
				<td>메인상단</td>
				<td>Hello World!  Good Morning!</td>
				<td>[치환코드]</td>
				<td>
					<a href="./banner_register.php?sno=8" class="btn btn-white btn-sm" role="button">수정</a>
				</td>
				<td>
					<a href="./banner_register.php?sno=8" class="btn btn-white btn-sm" role="button">삭제</a>
				</td>
			</tr>
			<tr>
				<td>
					<input name="sno[]" type="checkbox" value="8">
				</td>
				<td>1</td>
				<td>메인상단</td>
				<td>Hello World!  Good Morning!</td>
				<td>[치환코드]</td>
				<td>
					<a href="./banner_register.php?sno=8" class="btn btn-white btn-sm" role="button">수정</a>
				</td>
				<td>
					<a href="./banner_register.php?sno=8" class="btn btn-white btn-sm" role="button">삭제</a>
				</td>
			</tr>
			</tbody>
		</table>
		<div class="center">
			<nav>
				<ul class="pagination pagination-sm">
					<li class="active"><span>1</span></li>
				</ul>
			</nav>
		</div>
	</form>
</div>
```

###### 최종 화면

![admin추가](/images/post/godomall10.gif)
