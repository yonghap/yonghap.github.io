---
layout: post
title: "jQuery 폼 컨트롤 정리 (input, radio, checkbox)"
date : 2022-08-30
categories: [jquery]
tags: [jquery]
---

jQuery를 사용한 폼 요소의 컨트롤을 정리해 보겠습니다.\
폼 요소는 input text, radio, checkbox, select 입니다.

#### Input Text

```html
<input type="text" id="text">
```

```script
$('#text').val(); // 값 가져오기
$('#text').val('Input text'); // 값 설정하기
```

#### Radio

```html
<input type="radio" name="fruits" value="orange" checked="checked">
<input type="radio" name="fruits" value="banana">
<input type="radio" name="fruits" value="apple">
```

```javascript
$('[name=fruits]:checked').val(); // 체크된 값 가져오기 "orange"
$('[name=fruits]').val('apple').prop('checked',true); // 체크하기
$('[value=apple]').prop('checked',true); // 체크하기
$('[value=apple]').attr('checked','checked'); // 체크하기
$('[value=apple]').is(':checked'); // 체크 여부 확인
```

attr()과 prop()은 사용하는 경우가 다릅니다.
일반적으로 속성에 선언된 텍스트 그 자체를 의미할때는 attr()을 사용하고,
radio나 checkbox처럼 요소의 상태의 변경을 의미할때는 prop()을 사용합니다.

#### Checkbox

```html
<input type="checkbox" id="fruit1" name="fruits" value="apple" checked="checked">
<input type="checkbox" id="fruit2" name="fruits" value="banana">
<input type="checkbox" id="fruit3" name="fruits" value="orange">
```

```javascript
$('[name=fruits]:checked').val(); // 첫번째 체크 값 가져오기
$('#fruit2').prop('checked',true); // 1개 체크 'banana'
$('#fruit2').is(':checked'); // 체크 여부 확인
$('[name=fruits]').each(function() {
	$(this).prop('checked',true); // 모든 체크박스 체크
	$(this).is(':checked'); // 모든 체크박스 체크 여부 확인
});
$('[name=fruits]').val('banana').prop('checked',true); // 모든 체크박스 체크
```

checkbox는 radio처럼 val()로 선택해서 체크할 수 없습니다.
모든 체크박스가 선택됩니다.

#### Select

```html
<select name="select" id="select">
	<option value="#" selected="selected">Select</option>
	<option value="orange">Orange</option>
	<option value="apple">Apple</option>
	<option value="Mango">Mango</option>
</select>
```

```javascript
$('#select option:selected').val(); // 선택된 값 가져오기
$('#select').val(); // 선택된 값 가져오기
$('#select').val('orange').prop('selected',true); // 선택 하기 'orange'
$('#select').val('apple'); // 선택 하기 'apple'
if ( $('#select').val() == '' ) {
	console.log('값이 없습니다'); // 선택 여부 확인
}
```