---
title: '[TIL] Tailwindcss Install'
date: 2024-06-12T16:52:17+09:00
weight: 1
# aliases: ["/first"]
categories: ["seocho"]
tags: ["에이블런", "서초구 4차 산업 소프트웨어 과정", "TIL", "Today I Learned", "tailwindcss"]
author: "berry"
# author: ["Me", "You"] # multiple authors
showToc: true
TocOpen: false
draft: true # want to draft : true
hidemeta: false
comments: false
description: "Desc Text."
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
    Text: "Suggest Changes" # edit text
    appendFilePath: true # to append file path to Edit link
---

> # Today, I learned :grin:

## 1. dir 설정

```bash
mkdir tw
mkdir tw/src
cd tw
# package.json 파일 생성
npm init -y
```

## 2.tailwind cli 설치 및 세팅

```bash
npm install -D tailwindcss
npx tailwindcss init
```

## 3.tailwind.config.js 파일 수정

`module exports` > `content` 에 `["./src/**/*.{html,js}"]` 추가

## 4. src/input.css 파일 수정

```css
@tailwind base;
@tailwind components;
@tailwind utilities;
```

## 5. 실행하기

```bash
# tw 디렉토리에서 실행
npx tailwindcss -i ./src/input.css -o ./dist/output.css --watch

# 혹은 package.json에 script 추가
"dev": "tailwindcss -i ./src/input.css -o ./dist/output.css --watch"

npm run dev
```

> # Want to more about :sob:

-   emmet 문법을 좀 익혀야 할 것 같다.

> # ref :link:

-   [emmet-cheatsheet](https://docs.emmet.io/cheat-sheet/)
