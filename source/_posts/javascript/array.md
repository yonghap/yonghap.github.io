---
layout: post
title: "배열(Array) 가공 정리"
date : 2022-11-28
categories: [javascript]
tags: [javascript]
---

Javascript에서 자주 사용하는 배열(Array) 가공을 정리해 봅니다.

### Searching

#### indexOf

배열에서 지정된 요소의 위치값을 반환합니다.
값이 없으면 -1을 반환합니다.

```
const array1 = [1,2,3,4,5];
const result = array1.indexOf(4);
// 3
```

#### map

결과를 모아 (새로운 배열)을 반환합니다.
map은 mapping의 의미를 가지고 있습니다.

```
const array1 = [1,3,5,6,7];
const result = array1.map(x => x * 2); 
// [2,6,10,12,14]
```

#### filter

조건을 통과하는 (새로운 배열)을 만듭니다.

```
const array1 = [1,3,4,7,9];
const result = array1.filter(x => x % 3 === 0);
// [3,9]
```

#### find

조건을 통과하는 첫 번째 요소의 값을 반환합니다.

```
const array1 = [1,3,5,7,9,10];
const result = array1.find(x => x % 2 === 0);
// 10
```

#### findIndex

조건을 통과하는 첫 번째 요소의 인덱스를 반환합니다.
```
const array1 = [1,2,3,4,5];
const result = array1.findIndex(x => x % 2 === 0);
// 1
```

#### every

모든 요소에 대해 조건을 만족하는지 검사합니다.
하나라도 만족하지 못하면 false를 반환합니다.

```
const array1 = ['Apple','Orange','Banana'];
const array2 = ['Apple','Apple','Apple'];
const result1 = array1.every( x => x === 'Apple'); // false
const result2 = array2.every( x => x === 'Apple'); // true
```

#### some
모든 요소에 대해 조건을 만족하는지 검사합니다.
하나라도 만족하면 true를 반환합니다.

```
const array1 = ['Mango','Orange','Banana'];
const array2 = ['Mango','Orange','Apple'];
const result1 = array1.some( x => x === 'Apple'); // false
const result2 = array2.some( x => x === 'Apple'); // true
```


### Slice

#### Slice

기존 배열을 잘라서 (새로운 배열)을 만듭니다.
end 인덱스는 포함하지 않습니다.

```
const array1 = [1,3,5,7,9,10,12];
const result = array1.slice(1,4);
// [3,5,7]
```

#### Splice

배열의 기존 요소를 삭제,교체,추가 합니다.
(기존의 배열)을 변경합니다.

```
const array1 = [1,2,4,5];
array1.splice(2,0,3);
[1,2,3,4,5]
```

```
const array1 = [1,2,3,'a',4,5];
array1.splice(3,1);
[1,2,3,4,5]
```

### Mutations

#### join

배열을 모두 연결해 하나의 문자열로 만듭니다.

```
const array1 = ['Apple','Orange','Banana'];
const result1 = array1.join(''); // AppleOrangeBanana
const result2 = array1.join('-'); // Apple-Orange-Banana
```

#### push

배열에 요소를 추가하며 배열의 길이를 반환합니다.

```
const array1 = ['Apple','Orange']; // ['Apple','Orange','Banana']
const result = array1.push('Banana'); // 3
```

#### shift

첫 번째 요소를 제거하고, 그 요소를 반환합니다.

```
const array1 = ['Apple','Orange','Banana']; // ['Orange','Banana']
const result = array1.shift(); // Apple
```

#### pop

마지막 요소를 제거하고, 그 요소를 반환합니다.

```
const array1 = ['Apple','Orange','Banana']; // ['Apple','Orange']
const result = array1.pop(); // Banana
```

#### concat

배열을 합칩니다.


```
const array1 = ['Mango','Orange','Banana'];
const array2 = ['Grape','Apple'];
const result = array1.concat(array2);
// ['Mango','Orange','Banana','Grape','Apple']
```
