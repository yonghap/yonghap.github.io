---
layout: post
title: "Vue + Nuxt 날씨 서비스 만들기 – 3.Router와 Store 세팅"
date : 2022-11-01
categories: [vue]
tags: [vue]
---

### 1.Router 세팅

페이지 이동을 담당하는 라우터를 세팅하겠습니다.
Nuxt에서는 폴더구조에 따라 자동으로 라우팅을 지원합니다
아래와 같이 폴더 구조를 만듭니다.

```
/pages
 └location
   _id.vue
 index.vue
```

간단한 구조지만 아래와 같은 라우팅을 선언한 것과 동일합니다.

```
routes: [
	{
		name: 'index',
		path: '/',
		component: 'pages/index.vue'
	},
	{
		name: 'location',
		path: '/location/:id?',
		component: 'pages/location/_id.vue'
	},
]
```

/(루트)로 접근시 index.vue 파일을 보여주고,
/location/지역명 으로 접근시 _id.vue 파일을 보여줍니다.

### 2.Store 세팅

서비스에서 상태관리 요소를 세팅하겠습니다.
일반 페이지에서 data로 사용할 수도 있지만 추후 기능 추가나 유지보수를 위해서 store로
관리하도록 하겠습니다.


#### state

state에서 관리할 요소는 크게 3가지입니다.

> **appid** : Open API 호출에 사용할 App ID
> **currentLocation** : 현재 지역 정보 (영문명, 한글명, 좌표)
> **locations** : 사용할 지역 리스트 (서울,부산,광주,대전,강릉)

```
appid: '***',
currentLocation: {
	nameeng: 'Seoul',
		namekor: '서울',
		lat: '37.5683',
		lon: '126.9778'
},
locations: [
	{
		nameeng: 'Seoul',
		namekor: '서울',
		lat: '37.5683',
		lon: '126.9778'
	},
	{
		nameeng: 'BuSan',
		namekor: '부산',
		lat: '35.138311',
		lon: '129.0216844'
	},
	{
		nameeng: 'GwangJu',
		namekor: '광주',
		lat: '35.1594477',
		lon: '126.8446427'
	},
	{
		nameeng: 'DaeJeon',
		namekor: '대전',
		lat: '36.350461',
		lon: '127.3826247'
	},
	{
		nameeng: 'GangNeung',
		namekor: '강릉',
		lat: '37.7519967',
		lon: '128.8059146'
	},
]
```

#### getters

state를 가져오는 getters는 현재 지역 정보만 가져옵니다.

```
export const getters = {
	getCurrentLocation : state => {
		return state.currentLocation;
	}
}
```

#### mutations

state를 바꾸는 mutations는 현재 지역 정보만 변경합니다.


```
export const mutations = {
	setCurrentLocation(state, payload) {
		state.currentLocation = payloca;
	}
}
```

#### actions

actions에는 3가지 요소가 들어가며 api를 호출합니다.
날씨 정보, 대기 정보, 위치 정보 api를 사용합니다.
형태는 모두 비슷합니다.

```
async fetchWeatherData({commit, state}, geoInfo) {
	return new Promise((resolve, reject) => {
		const prm = {
			params: {
				lat: geoInfo.lat,
				lon: geoInfo.lon,
				exclude: '',
				appid: state.appid
			}
		}
		this.$axios.$get('https://api.openweathermap.org/data/2.5/onecall', prm)
			.then((result) => {
				resolve(result);
			})
			.catch(err => {
				reject(err);
			})
	})
}
```

라우터와 스토어 세팅이 끝났습니다.
스토어의 actions에서 가져온 api 정보를 바탕으로
이제 view 페이지에 데이터를 뿌려 보겠습니다.
