---
layout: post
title: "잘 알려지지 않은 CSS 속성들"
date : 2022-09-19
categories: [css]
tags: [css]
---

잘 알려지지 않은 CSS 속성들 정리입니다.
모바일이나 모던 브라우저에서는 활용해볼만 합니다.
브라우저 지원 여부는 아래 사이트에서 확인할 수 있습니다.
<a href="https://caniuse.com/" target="_blank" rel="noopener noreferrer">https://caniuse.com</a>


#### user-select

드래그하면 나타나는 텍스트 선택영역에 대한 동작을 정의합니다.

- **auto** : 기본값
- **none** : 선택하지 않음
- **text** : 텍스트 선택 동작
- **all** : 모두 선택

<iframe height="450" style="width: 100%;" scrolling="no" title="user-select" src="https://codepen.io/yonghap/embed/WNxPBKY?height=265&theme-id=dark&default-tab=html,result" frameborder="no" loading="lazy" allowtransparency="true" allowfullscreen="true">

</iframe>

#### touch-action

모바일에서 동작하는 터치액션을 정의합니다.
모바일에서만 확인할 수 있습니다.

- **auto** : 기본값
- **none** : 터치 불가
- **pan-x** : x축으로만 스크롤 가능
- **pan-y**
- **pan-left** : 왼쪽으로만 스크롤 가능
- **pan-right**
- **pan-up**
- **pan-down**
- **pinch-zoom** : 핀치 줌 가능
- **manipulation** : 터치와 핀치 줌만 가능
- **pan-x pan-y** : 여러 액션 가능

<iframe height="400" style="width: 100%;" scrolling="no" title="touch-action" src="https://codepen.io/yonghap/embed/NWroVVo?height=265&theme-id=dark&default-tab=html,result" frameborder="no" loading="lazy" allowtransparency="true" allowfullscreen="true">
</iframe>

#### object-fit

이미지나 비디오 요소의 콘텐츠 크기를 부모요소에 어떻게 맞춰지는지 지정합니다.

- **fill** : 초기값으로 부모 요소에 넓이와 높이를 맞춤
- **cover** : 콘텐츠의 비율을 유지하면서 부모 요소를 가득 채움
- **contain** : 콘텐츠의 비율을 유지하면서 부모 요소에 딱 맞게 채움
- **none** : 조절하지 않음
- **scale-down** : none과 contain 중 콘텐츠의 크기가 더 작은 값을 적용

<iframe height="400" style="width: 100%;" scrolling="no" title="touch-action" src="https://codepen.io/yonghap/embed/XWNXmNV?height=265&theme-id=dark&default-tab=html,result" frameborder="no" loading="lazy" allowtransparency="true" allowfullscreen="true">
</iframe>

#### will-change

transform, opacity처럼 자주 변하는 속성을 선언하여, 트랜지션때 부드러운 효과를 줄 수 있습니다. 
남발하게 될 경우 성능이 저하될 수 있으니 유의가 필요합니다.

```
<style>
	will-change: auto; /* 기본 값 */
	will-change: scroll-position;
	will-change: contents;
	will-change: transform;        /* Example of <custom-ident> */
	will-change: opacity;          /* Example of <custom-ident> */
	will-change: left, top;        /* Example of two <animateable-feature> */

	/* 전역 값 */
	will-change: inherit;
	will-change: initial;
	will-change: unset;
</style>
```

#### list-style-position

리스트 아이템 앞에 오는 블릿들의 위치를 지정합니다.

```
<style>
	list-style-position:inside; 
	list-style-position:outside; 
</style>
```

#### overflow-wrap

한글 문서에서 word-break:keep-all 을 통해 단어 줄바꿈을 사용합니다.
하지만 한 단어의 길이가 너무 길다면, 넘쳐버리게 됩니다.
이를 방지하기 위해 사용합니다.

```
<style>
	overflow-wrap:normal; /* 기본값 */
	overflow-wrap:break-word; /* 단어 줄바꿈 */
</style>
```