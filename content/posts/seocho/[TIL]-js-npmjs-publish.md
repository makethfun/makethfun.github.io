---
title: '[TIL] Js Npmjs Publish'
date: 2024-06-05T16:38:19+09:00
weight: 1
# aliases: ["/first"]
categories: ["seocho"]
tags: ["에이블런", "서초구 4차 산업 소프트웨어 과정", "TIL", "Today I Learned", "npmjs"]
author: "berry"
# author: ["Me", "You"] # multiple authors
showToc: true
TocOpen: false
draft: true            # want to draft : true
hidemeta: false
comments: false
description: "publish private packages"
canonicalURL: "https://canonical.url/to/page"
disableHLJS: true # to disable highlightjs
disableShare: false
disableHLJS: false
hideSummary: false
searchHidden: true
ShowReadingTime: true
ShowBreadCrumbs: true
ShowPostNavLinks: true
ShowWordCount: false
ShowRssButtonInSectionTermList: true
UseHugoToc: true
# cover:
#     image: "<image path/url>" # image path/url
#     alt: "<alt text>" # alt text
#     caption: "<text>" # display caption under cover
#     relative: false # when using page bundles set this to true
#     hidden: true # only hide on current single page
editPost:
    URL: "https://github.com/makethfun/content"
    Text: "패키지를 만들어보자" # edit text
    appendFilePath: true # to append file path to Edit link
---

# Today, I learned :grin:

## npm package publish

### 1. 가입 및 로그인

> https://npmjs.com

### 2. 해당 폴더에서 package.json 파일 만들기

```bash
// 해당 폴더 이동 후

npm init -y
# git repo는 독립적으로 생성

cat package.json
```

### 3. package.json 파일 수정

```js
// package.json
{
    "name": "makethseocho", // npm info <pkg> 이름 중복 확인
    "version": "0.1.0-beta.1", // version 설정
    "description": "js study",
    "main": "index.js",  // main entry 지정
    "scripts": {
        "test": "echo \"Error: no test specified\" && exit 1"
    },
    "keywords": [
        "js"
    ],
    "author": "makethfun",
    "license": "ISC",
    "dependencies": {
        "moment": "^2.30.1"
    }
}

```

### 4. npm login & publish

```bash
> npm login

npm notice Log in on https://registry.npmjs.org/
Login at:
https://www.npmjs.com/login?next=/login/cli/78abe2ef-0b72-440d-98bb-43225ad5bfcf
Press ENTER to open in the browser...

Logged in on https://registry.npmjs.org/.

```

### 5. deploy

```bash
# package.json 파일의 version을 바꾼 후,
npm publish --access public
```

> # Want to more about :sob:

-   ESM 방식의 module import를 좀 더 익혀야 할듯?
-   npmjs에 패키지를 만들 때 이름과 버전 주의할 것 (가끔 안되는 것들이 있음)

> # ref :link:
