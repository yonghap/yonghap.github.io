---
layout: post
title: "다크 모드 파비콘(Darkmode Favicon)"
date : 2022-09-13
categories: [html]
tags: [html]
---

일반적으로 파비콘을 아래와 같이 적용합니다.

```
<link rel="icon" href="favicon.ico" sizes="any">
```

최근에는 다크 모드를 쓸 수 있는 브라우저가 많아졌습니다. 
테마 기반 크롬, 파이어폭스, 웨일에서 모두 지원하고 있으며 야간 작업시에 필히 사용하는 모드입니다. 
이에 따라 파비콘도 다르게 적용할 수 있습니다. 
svg 이미지 파일을 사용합니다.

![1](/images/post/favi.jpg)


### 1.html 소스 작성

```
<link rel="icon" href="favicon.svg" type="image/svg+xml">
```

### 2.favicon.svg 소스 작성

```
<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 40 40">
    <style>
        @media (prefers-color-scheme: dark) {
            #circle { fill:yellow; stroke:white }
        }
    </style>
    <!-- Circle -->
    <circle id="circle" cx="20" cy="20" r="17" stroke="red" fill="blue" stroke-width="6"/>
</svg>
```

###### result

![1](/images/post/favi2.jpg)

svg 파일내에 style 선언을 통해 다크 모드에 대한 색상을 정의해 줍니다.
추가로 쉽게 svg 형태로 만들 수 있는 사이트가 있습니다.

<a target="_blank" href="https://jakearchibald.github.io/svgomg/" rel="noopener">https://jakearchibald.github.io/svgomg</a>