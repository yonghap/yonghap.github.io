---
layout: post
title: "웹폰트(Webfont) 사용법 정리"
date : 2022-07-27
categories: [css]
tags: [css]
---


![can](/images/post/webfont.png)

```css
@font-face {
	font-family: NotoSans;
	src: url(NotoSans.eot); /*IE 호환성 보기*/
	src:
		local("NotoSans"), /* 로컬 서체 Full Name */
		local(※), /* IE fix */
		url(NotoSans.eot?#iefix) format('embedded-opentype'), /*IE 6 - 8*/
		url(NotoSans.woff2) format('woff2'), /*WOFF2*/
		url(NotoSans.woff) format('woff'), /*WOFF*/
		url(NotoSans.ttf) format('truetype');				
}
```

자주 사용하는 웹폰트 소스입니다. 
font-face 규칙만 해도 너무나 많습니다.
한가지씩 뜯어보면서 필요 없는 것은 빼겠습니다.

##### 1.브라우저별 다운로드 파일

**IE6 ~ IE8**는 NotoSans.eot?#iefix 부분의 파일이 다운로드 됩니다. 
**IE 호환성 보기**는 처음 src로 선언된 NotoSans.eot 다운로드 됩니다. 
**IE9 이상**은 NotoSans.eot?#iefix 부분의 파일이 다운로드 됩니다. 
iefix 구문을 지우고 local(※) 구문을 사용하면 NotoSans.woff가 다운로드 됩니다. 
**모던 브라우저**는 지원여부에 따라 woff2, woff 순으로 다운로드 됩니다.

##### 2.웹폰트 처리 프로세스

###### src: url(NotoSans.eot)

IE6 ~ IE8에서 eot 글꼴을 요청하여 표시합니다.

###### local("NotoSans")

로컬 폰트 이름을 표시합니다.
웹폰트와 로컬 폰트와의 모양이 상이할 수 있으므로 2바이트 문자를 사용하기도 합니다.
IE6 ~ IE8에서 local 구문을 해석하지 못하므로 이후 요청은 무시됩니다.

###### url(NotoSans.eot?#iefix) format('embedded-opentype')

IE6 ~ IE8에서 포맷명을 인식하지 못합니다. 
url(NotoSans.eot) format('embedded-opentype') 
위 구문을 사용했을때 404 에러가 납니다. 
따라서 파일명 뒤에 물음표를 추가하여 뒤에 구문을 모두 쿼리문으로 인식하게 합니다. 
브라우저에서는 NotoSans.eot? 파일이 다운로드 됩니다.

###### url(NotoSans.eot)

IE 호환성 보기 모드에서는 위 물음표 꼼수, format, local 구문을 인식하지 못합니다. 
따라서 src를 따로 구분하여 작성해 줍니다.

###### local(※)

IE에서 이 구문을 인식못하는 특징을 활용하여, 
url(NotoSans.eot) 구문을 사용하고 iefix 구문 대신 사용합니다.

###### url(NotoSans.woff) format('woff')

브라우저 지원여부에 따라 해당 파일을 다운로드 합니다.

### 브라우저별 방탄 소스


#### 모던 브라우저 + IE 지원 코드 1 (eot파일 사용)

```css
@font-face {
	font-family: NotoSans;
	src: url(NotoSans.eot); /*IE 호환성 보기*/
	src:		
		url(NotoSans.eot?#iefix) format('embedded-opentype'), /*IE 6 - 8*/
		url(NotoSans.woff2) format('woff2'), /*WOFF2*/
		url(NotoSans.woff) format('woff'), /*WOFF*/
		url(NotoSans.ttf) format('truetype');				
}
```
IE는 eot, 모던 브라우저는 woff2를 사용합니다.


#### 모던 브라우저 + IE 지원 코드 2 (woff 파일 사용)

```css
@font-face {
	font-family: NotoSans;
	src: url(NotoSans.eot); /*IE6~8,호환성 보기*/
	src:		
		local(※), /* IE fix */
		url(NotoSans.woff2) format('woff2'), /*WOFF2*/
		url(NotoSans.woff) format('woff'), /*WOFF*/
		url(NotoSans.ttf) format('truetype');				
}
```
IE6~8에서는 eot, IE9+에서는 woff, 모던 브라우저에서는 woff2를 사용합니다.

#### Ethan의 방탄 코드

```css
@font-face {
	font-family: 'Noto Sans KR';
	src:
		url('./common/css/fonts/NotoSans-Light.eot?#iefix') format('embedded-opentype'),
		url('./common/css/fonts/NotoSans-Light.woff2') format('woff2'),
		url('./common/css/fonts/NotoSans-Light.woff') format('woff');
}
```

Ethan에서 제안한 웹폰트 방탄을 활용한 코드입니다.
IE9+ src에 글꼴 형식을 두개 이상 로드하려고 하면 404 오류가 발생합니다. 
이유는 여는 괄호 사이의 모든것을 파일 하나로 로드하려고 하기 때문입니다. 
따라서 물음표를 추가하여 나머지 문자열은 쿼리 스트링으로 인식하게 합니다 
나머지 브라우저는 사양에 맞게 다운로드 됩니다. 
다만 IE11의 브라우저 에뮬레이션 변경으로 인한 테스트에는 제대로 동작하지 않았습니다. 

<a href="https://blog.fontspring.com/2011/02/the-new-bulletproof-font-face-syntax/" target="_blank" rel="noopener">https://blog.fontspring.com/2011/02/the-new-bulletproof-font-face-syntax/</a>