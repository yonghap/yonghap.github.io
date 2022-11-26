---
layout: post
title: "Vue + Nuxt 날씨 서비스 만들기 - 1.설치"
date : 2022-09-26
categories: [vue]
tags: [vue]
---

Vue와 Nuxt로 간단한 날씨 서비스를 만들어 보려 합니다.
Nuxt를 이용하여 Vue에서도 SSR을 지원할 수 있습니다.


SSR(Server Side Rendering)에 관한 자세한 정보는 Vue에서도 소개해주고 있습니다.
<a href="https://ssr.vuejs.org/#what-is-server-side-rendering-ssr" target="_blank" rel="noopener noreferrer">https://ssr.vuejs.org/#what-is-server-side-rendering-ssr</a>
단순 메타태그만을 위한 모듈이나 prerender-spa-plugin을 사용할 순 있지만 완벽하진 않습니다.
그래서 NuxtJS를 사용합니다.
참고로 국내 포털사이트에서는 JS로 변경된 메타태그를 체크 안하지만 구글에서는 지원해주고 있습니다.


### 1.설치

#### create-nuxt-app 활용 설치

공식 사이트에서 설치법을 확인할 수 있습니다.
create-nuxt-app을 활용합니다.
<a href="https://ko.nuxtjs.org/" target="_blank" rel="noopener noreferrer">https://ko.nuxtjs.org/</a>

```bash
npm init nuxt-app <project-name>
```

설치 명령을 내리면 여러가지 옵션을 지정할 수 있습니다.
저는 Npm 사용, JavaScript, UI 프레임워크 사용안함, Axios/PWA, Jest, SSR을 선택했습니다.
프로젝트 성격에 따라 선택하면 됩니다.
상세한 옵션을 아래 create-nuxt-app에서 확인할 수 있습니다.
<a href="https://github.com/nuxt/create-nuxt-app/" target="_blank" rel="noopener noreferrer">https://github.com/nuxt/create-nuxt-app/</a>

#### 수동 설치

직접 프로젝트 폴더를 생성하여 설치할 수도 있습니다.

```bash
mkdir <project-name>
cd <project-name>

touch package.json
```

프로젝트 폴더를 만들고 들어간 뒤 package.json 파일을 만듭니다.

```json
{
  "name": "my-app",
  "scripts": {
    "dev": "nuxt",
    "build": "nuxt build",
    "generate": "nuxt generate",
    "start": "nuxt start"
  }
}
```

내용을 입력합니다.

```bash
npm install
```




### 2.실행

```bash
cd <project-name>
npm run dev
```

![flex](/images/post/vue01.gif)
