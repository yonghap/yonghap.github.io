---
layout: post
title: "CSS Flex(Flexible Box) 정리"
date : 2022-09-16
categories: [css]
tags: [css]
---

우리는 가로형 레이아웃을 잡을 때 float, inline-block을 사용했습니다.
또는 극단적으로 absolute 포지션을 사용하기도 했습니다.
이는 구현은 가능할 수 있으나 css의 의미있는 사용도 안될뿐더러 불편하거나 유연하지 못합니다.

float은 콘텐츠를 부유해서 보여주고 inline-block은 다른 콘텐츠와의 배치를 결정하는데 쓰입니다.
absolute 포지션을 절대적인 위치값을 가진 요소를 나타내는데 쓰입니다.

Flex는 요소의 정렬과 배치를 행과 열로 구분하여 효과적으로 할 수 있는 CSS 레이아웃 모델입니다.

![flex](/images/post/flex1.gif)


IE10~11에서 일부 지원합니다.
기타 모던 브라우저에서는 모두 지원합니다.

### 1.기본 HTML 구조
아래와 같은 기본 HTML 구조로 진행합니다.

#### HTML
```
<div class="box">
	<div class="item item--1">
		1 <br>
		Lorem <br>
		ipsum
	</div>
	<div class="item item--2">
		2<br>
		Lorem ipsum dolor sit amet.
	</div>
	<div class="item item--3">
		3 <br>
		Lorem ipsum dolor sit amet, <br>
		consectetur adipisicing elit. Hic, voluptatem?
	</div>
	<div class="item item--4">
		4 <br>
		Lorem ipsum dolor sit amet, consectetur adipisicing elit.<br>
		iste molestias reiciendis sint suscipit!
	</div>
	<div class="item item--5">
		5 <br>
		Lorem ipsum dolor sit amet, <br>
		consectetur adipisicing.
	</div>
</div>
```

##### CSS
```css
<style>
	.box {
		display:flex;
	}
	.item {
		padding:20px 10px;
		color:#fff;
	}
	.item:first-letter {font-size:50px}
	.item--1 {background:#0080cc;}
	.item--2 {background:#cc3a2f;}
	.item--3 {background:#01cc49;}
	.item--4 {background:#cca514;}
	.item--5 {background:#9a25cc;}
</style>
```
> **.box(Flex Container)** : Flex Item을 감싸고 있는 영역입니다.
> **.item(Flex Item)** : Flex Item 입니다.

Flex에서 사용할 수 있는 CSS는 컨테이너에 적용하는 속성과, 아이템에 적용하는 속성으로 나뉘어 있습니다.

##### RESULT

###### 화면에 넘치지 않을 때
![flex](/images/post/flex2.gif)
###### 화면에 넘치지 않을 때
![flex](/images/post/flex3.gif)

flex 속성 추가만으로 float이나 inline-block으로 만들었던 레이아웃을 쉽게 만들 수 있습니다.
요소의 넓이에 따라 배치되며, 넘칠때에는 아래로 떨어지지 않고 자연스럽게 줄어듭니다.

### 2.컨테이너에 적용하는 Flex

#### - flex-direction:(direction, 기본값 row)
item 요소의 정렬 방향을 결정합니다.

```
<style>
	.box {
		flex-direction:row-reverse; //요소 방향 -> (기본값)
		flex-direction:row-reverse; //요소 방향 <-
		flex-direction:column; //요소 방향 ↓
		flex-dirction:column-reverse; //요소 방향 ↑
	}
</style>
```

###### flex-direction:row
![flex](/images/post/flex4.gif)
###### flex-direction:row-reverse
![flex](/images/post/flex5.gif)
###### flex-direction:column
![flex](/images/post/flex6.gif)
###### flex-direction:column-reverse
![flex](/images/post/flex7.gif)

#### - flex-wrap:(wrap,nowrap, 기본값 nowrap)
넘치는 item 요소에 대하여 표시 방법을 결정합니다.

```
<style>
	.box {
		flex-wrap:wrap; //넘칠 경우 줄바꿈 합니다.
		flex-wrap:nowrap; //컨테이너 폭에 맞게 줄어듭니다.
	}
</style>
```

###### flex-wrap:wrap
![flex](/images/post/flex8.gif)

#### - flex-flow:(direction wrap)
아래와 같이 축약 속성으로 사용합니다.
```
<style>
    .box {
        flex-flow:row wrap;
        flex-flow:column nowrap;
        flex-flow:row-reverse wrap;
        flex-flow:column-reverse nowrap;
    }
</style>
```
#### - justify-content:(align)
메인축 방향의 아이템들을 정렬 방식 속성입니다.
메인축과 교차축은 flex-direction에 따라 달라집니다.
정렬 확인을 위해 아이템에 flex-basis로 넓이값을 주었습니다.
```
<style>
	.box {
		display:flex;
		justify-content:flex-start;
		justify-content:flex-end;
		justify-content:center;
		justify-content:space-between;
		justify-content:space-around;
		justify-content:space-evenly;
	}
	.item {
		flex-basis:150px;
		padding:20px 10px;
		color:#fff;
	}
</style>
```
###### justify-content:flex-start

![flex](/images/post/flex9.gif)

초기값입니다.

###### justify-content:flex-end

![flex](/images/post/flex10.gif)

메인축의 끝부터 정렬 합니다.

###### justify-content:flex-center

![flex](/images/post/flex11.gif)

가운데 정렬합니다.

###### justify-content:space-between

![flex](/images/post/flex12.gif)

아이템을 좌우끝에 붙이고 나머지 공간은 균등 분배합니다.

###### justify-content:space-around

![flex](/images/post/flex13.gif)

아이템을 감싸고 있는 여백을 균등 분배합니다.

###### justify-content:space-evenly

![flex](/images/post/flex14.gif)

모든 여백을 균등 분배합니다.


#### - align-items:(align)
교차축 방향의 아이템들을 정렬 방식 속성입니다.
이해하기 쉽게 justify-content는 가로 정렬, align-items는 세로 정렬로 이해합니다.

```
<style>
	.box {
		display:flex;
		align-items:stretch;
		align-items:flex-start;
		align-items:flex-end;
		align-items:center;
		align-items:baseline;
	}
	.item {
		flex-basis:150px;
		padding:20px 10px;
		color:#fff;
	}
</style>
```
###### align-items:stretch

![flex](/images/post/flex15.gif)

교차축을 꽉채워서 정렬합니다.

###### align-items:flex-start

![flex](/images/post/flex16.gif)

교차축 시작점으로 정렬합니다.

###### align-items:flex-end

![flex](/images/post/flex17.gif)

교차축 끝점으로 정렬합니다.

###### align-items:center

![flex](/images/post/flex18.gif)

교차축 중앙에 정렬합니다.

###### align-items:baseline

![flex](/images/post/flex19.gif)

텍스트 베이스라인 기준으로 정렬합니다.


#### - align-content:(align)
flex-wrap 속성으로 줄바꿈된 아이템들을 정렬합니다.
컨테이너에 높이값을 주었고, 아이템의 줄바꿈 되기위해 flex-basis 값을 주었습니다.

```
<style>
	.box {
		display:flex;
		height:600px;
		flex-wrap:wrap;
		align-content:stretch;
		align-content:flex-start;
		align-content:flex-end;
		align-content:center;
		align-content:space-between;
		align-content:space-around;
		align-content:space-evenly;
	}
	.item {
		flex-basis:320px;
		padding:20px 10px;
		color:#fff;
	}
</style>
```

###### align-content:stretch

![flex](/images/post/flex20.gif)

교차축을 꽉채워서 정렬합니다.

###### align-content:flex-start

![flex](/images/post/flex21.gif)

교차축을 시작점으로 정렬합니다.

###### align-content:flex-end

![flex](/images/post/flex22.gif)

교차축을 끝점으로 정렬합니다.

###### align-content:center

![flex](/images/post/flex23.gif)

교차축을 중앙으로 정렬합니다.

###### align-content:space-between

![flex](/images/post/flex24.gif)

아이템을 교차점 시작과 끝에 붙이고 나머지 공간은 균등 분배합니다.

###### align-content:space-around

![flex](/images/post/flex25.gif)

아이템을 둘레를 균등 분배합니다.

###### align-content:space-evenly

![flex](/images/post/flex26.gif)

모든 여백을 균등 분배합니다.


### 3.아이템에 적용하는 Flex

#### - flex-grow:(number, 기본값 0)
아이템이 공간내에서 가지는 비율을 결정합니다.
값은 px이 아닌 비율이며, 아이템들이 빈 공간이 없게 풀로 표시됩니다.

```
<style>
	.item--1 {
		flex-grow:3;
		background:#0080cc;
	}
	.item--2 {
		flex-grow:1;
		background:#cc3a2f;
	}
	.item--3 {
		flex-grow:2;
		background:#01cc49;
	}
	.item--4 {
		flex-grow:1;
		background:#cca514;
	}
	.item--5 {
		flex-grow:2;
		background:#9a25cc;
	}
</style>
```

![flex](/images/post/flex27.gif)

#### - flex-shrink:(number, 초기값 1)
아이템이 넘칠때 요소를 어떻게 처리할지 결정합니다.
flex-basis 속성과 같이 쓰입니다.
값이 0이라면 아이템이 넘쳐도 넓이가 flex-basis 값 밑으로 떨어지지 않습니다.
flex-grow는 확대 비율, flex-shrink는 축소 비율이라고 생각하면 쉽습니다.

```
<style>
	.box {
		display:flex;
		width:500px;
	}
	.item {
		flex-basis:150px;
		padding:20px 10px;
		color:#fff;
	}
	.item:first-letter {font-size:50px}
	.item--1 {
		flex-shrink:0;
		background:#0080cc;
	}
	.item--2 {
		flex-shrink:2;
		background:#cc3a2f;
	}
</style>
```

![flex](/images/post/flex28.gif)

컨테이너의 넓이값 500px을 주고, 각 아이템의 넓이는 flext-basis로 150px로 선언했습니다.
컨테이너의 넓이값을 넘어가게 되므로 각각의 아이템들을 500px내에서 유연하게 넓이값을 가지게 됩니다.
하지만 flex-shrink을 0으로 지정함으로써 넓이를 고정할 수 있습니다.

#### - flex-basis:(number, 초기값 auto)
아이템의 크기를 설정합니다.

```
<style>
	.box {
		display:flex;
	}
	.item {
		flex-basis:500px;
		padding:20px 10px;
		color:#fff;
	}
</style>
```

![flex](/images/post/flex29.gif)

flex-wrap가 선언되어 있지 않아서 넘치는 부분은 유연하게 넓이가 조절됩니다.

```
<style>
	.box {
		display:flex;
		flex-wrap:wrap;
	}
	.item {
		flex-basis:500px;
		padding:20px 10px;
		color:#fff;
	}
</style>
```



![flex](/images/post/flex30.gif)

flex-wrap가 선언되어 flex-basis에 적용된 넓이대로 표시됩니다.

#### - flex:(flex-grow, flex-shrink, flex-basis)
세 가지 속성을 한번에 선언할 수 있습니다.
선언한 매개변수 숫자에 따라 적용되는 속성이 다릅니다.

##### 값이 한 개일 때
숫자를 지정하면 flex-grow 입니다.
길이 또는 퍼센트를 지정하면 flex-basis입니다.
none, auto, initial 중 하나를 지정할 수 있습니다.

##### 값이 두 개일 때
첫 번째 값은 숫자이고 flex-grow입니다.
두 번재 값은 숫자를 지정하면 flex-shrink 입니다.
길이 또는 퍼센트, auto를 지정하면 flex-basis 입니다.

##### 값이 세 개일 때
flex-grow, flex-shrink, flex-basis 순입니다.

##### 기타
> **flex:initial** : flex:0 1 auto 동일
> **flex:auto** : flex:1 1 auto 동일
> **flex:none** : flex:0 0 auto 동일

#### - align-self:(align)
컨테이너에서 적용했던 align-items의 아이템 버전입니다.

```
<style>
	.box {
		display:flex;
	}
	.item {
		flex-basis:350px;
		padding:20px 10px;
		color:#fff;
	}
	.item--3 {
		align-self:center;
		background:#01cc49;
	}
</style>
```
###### align-self:center

![flex](/images/post/flex31.gif)


#### - order:(order)
아이템의 순서를 정합니다.
마크업 구조는 바뀌지 않습니다.

```
<style>
	.item--1 {
		order:4;
		background:#0080cc;
	}
	.item--2 {
		order:2;
		background:#cc3a2f;
	}
	.item--3 {
		align-self:center;
		order:1;
		background:#01cc49;
	}
	.item--4 {
		order:5;
		background:#cca514;
	}
	.item--5 {
		order:5;
		background:#9a25cc;
	}
</style>
```

![flex](/images/post/flex32.gif)