---
layout: post
title: "IR 기법 (이미지 대체 텍스트)"
date : 2022-09-01
categories: [html]
tags: [html]
---

IR 기법은 이미지를 대체하여 표시할 수 있는 기법을 말합니다.
이미지의 alt 값이 길거나 의미 있는 이미지를 배경으로 사용할 때 주로 사용합니다.
크게 4가지 방법이 있습니다.

#### default

기본 alt 속성을 활용하는 방법입니다.

```
<img src="picture.jpg" alt="사람이 의자에 앉아 책을 읽고 있는 모습">
```

다음과 같이 의미 없는 대체 텍스트는 지양합니다.

```
<img src="picture.jpg" alt="사람 이미지">
```

#### Phark Method

흔히 사용하는 텍스트를 날려버리는 방법입니다.

```
a {
	text-indent:-9999px;
}
```

#### WA IR

z-index를 활용하여 우선 순위를 내려 이미지 아래로 텍스트를 숨길 수도 있습니다.
태그를 추가해야 된다는 단점이 있고, position 속성에 따라 성능에 영향을 줄 수 있습니다.

```
button span {
	position:relative;
	z-index:-1;
}
```

#### 최신 H5BP (HTML5 Boilerplate)

H5BP나 부트스트랩에서 사용하는 방법입니다.

```
.sr-only {
	position: absolute;
	width: 1px;
	height: 1px;
	padding: 0;
	overflow: hidden;
	clip: rect(0, 0, 0, 0);
	white-space: nowrap;
	clip-path: inset(50%);
	border: 0;
}
```