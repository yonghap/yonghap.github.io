---
layout: post
title: "Responsive Table (반응형 테이블)"
date : 2022-09-06
categories: [html,css]
tags: [html,css]
---

모바일에서 데이터가 많은 테이블의 표시는 어렵습니다.
가독성을 높이기에는 콘텐츠가 길어져 지루하게 느껴질수도 있고, 쓸모없는 데이터라고 생각이 들수도 있습니다.
그렇다고 여러 데이터를 한번에 보여주기에는 화면이 너무 작습니다.
따라서 반응형 웹에서의 테이블도 데이터에 따라 적절한 방법을 찾아야 합니다.
가장 기본적인 데이터 테이블의 반응형 구축에 대해서 알아 보겠습니다.

#### 스크롤

테이블이 일정한 넓이를 가지며, 디바이스 사이즈가 작아질 경우 가로 스크롤 처리합니다.
데이터는 적지만 가로형태의 긴 테이블에서 유용합니다.

<iframe height="400" style="width: 100%;" scrolling="no" title="RWD Table" src="https://codepen.io/yonghap/embed/ExyZjvY?height=265&theme-id=dark&default-tab=html,result" frameborder="no" loading="lazy" allowtransparency="true" allowfullscreen="true">
  See the Pen <a href='https://codepen.io/yonghap/pen/ExyZjvY'>RWD Table</a> by Yonghap
  (<a href='https://codepen.io/yonghap'>@yonghap</a>) on <a href='https://codepen.io'>CodePen</a>.
</iframe>


#### 블럭

항목 및 데이터를 블럭 형태로 처리합니다.
데이터는 적지만 중요성이 높은 자료에 유용합니다.
항목 이름을 before 가상 선택자를 활용해 표시합니다.


<iframe height="400" style="width: 100%;" scrolling="no" title="Rwd Table" src="https://codepen.io/yonghap/embed/MWeJwEL?height=265&theme-id=dark&default-tab=css,result" frameborder="no" loading="lazy" allowtransparency="true" allowfullscreen="true">
  See the Pen <a href='https://codepen.io/yonghap/pen/MWeJwEL'>Rwd Table</a> by Yonghap
  (<a href='https://codepen.io/yonghap'>@yonghap</a>) on <a href='https://codepen.io'>CodePen</a>.
</iframe>

#### 가로 항목 고정

가로로 긴 형태의 테이블에 적합합니다.
항목을 고정시켜 확인하기 쉽게 합니다.

<iframe height="400" style="width: 100%;" scrolling="no" title="RWD Table" src="https://codepen.io/yonghap/embed/bGegdaM?height=265&theme-id=dark&default-tab=html,result" frameborder="no" loading="lazy" allowtransparency="true" allowfullscreen="true">
  See the Pen <a href='https://codepen.io/yonghap/pen/bGegdaM'>RWD Table</a> by Yonghap
  (<a href='https://codepen.io/yonghap'>@yonghap</a>) on <a href='https://codepen.io'>CodePen</a>.
</iframe>

#### 세로 항목 고정

항목은 적지만 긴 형태의 테이블에 적합합니다.
항목을 고정시켜 스크롤을 해도 어떤 항목인지 쉽게 확인 합니다.

<iframe height="400" style="width: 100%;" scrolling="no" title="RWD Table" src="https://codepen.io/yonghap/embed/wvWgaym?height=265&theme-id=dark&default-tab=html,result" frameborder="no" loading="lazy" allowtransparency="true" allowfullscreen="true">
  See the Pen <a href='https://codepen.io/yonghap/pen/wvWgaym'>RWD Table</a> by Yonghap
  (<a href='https://codepen.io/yonghap'>@yonghap</a>) on <a href='https://codepen.io'>CodePen</a>.
</iframe>


위 예제는 반응형 테이블의 방법중 하나입니다.
정답인 방법은 없으며 데이터에 따라 여러 방법을 선택하면 됩니다.