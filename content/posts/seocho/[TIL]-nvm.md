---
title: '[TIL] Nvm'
date: 2024-05-21T09:51:17+09:00
weight: 1
# aliases: ["/first"]
categories: ["seocho"]
tags: ["에이블런", "서초구 4차 산업 소프트웨어 과정", "TIL", "Today I Learned", "nvm", "node.js"]
author: "berry"
# author: ["Me", "You"] # multiple authors
showToc: true
TocOpen: false
draft: true            # want to draft : true
hidemeta: false
comments: false
description: "node version manager"
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

## 1. NVM ?
> nvm은 Node Version Manager로 Node.js의 버전을 관리하는 도구

- 협업이나 여러 프로젝트를 실행할 때 버전 차이로 인해 라이브러리나 프레임워크가 호환문제를 일으킬 수도 있으므로 같은 버전의 Node를 사용해 주는게 좋음

- 파이썬의 pyenv와 같은 역할

## 2. 설치방법


```bash
# download
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.7/install.sh | bash

# ~/.zshrc 나 ~/.bashrc에 추가
export NVM_DIR="$([ -z "${XDG_CONFIG_HOME-}" ] && printf %s "${HOME}/.nvm" || printf %s "${XDG_CONFIG_HOME}/nvm")"
[ -s "$NVM_DIR/nvm.sh" ] && \. "$NVM_DIR/nvm.sh" # This loads nvm

```

## 3. cmd

```bash
# node 버전 설치
nvm install <version>

# 최신 lts 버전 설치
nvm install --lts

# 설치된 node 목록 확인
nvm ls

# 설치할 수 있는 모든 node 버전 조회 
nvm ls-remote

# 특정 버전의 node 사용
nvm use <version>

# 현재 사용중인 버전 확인
nvm current

# node 설치 경로 확인
which node

# node 버전 삭제
nvm uninstall <version>

# 설치되어 있는 가장 최신버전의 node를 디폴트로 사용

nvm alias default node
```
> # Want to more about :sob:

- 오랫만에 node를 하려고 했더니 내 컴퓨터엔 v14.x.x가 설치되어 있었음
- 벌써 lts 버전이 v21.4.0이라니 앞으로 자주 활용해야 할 것 같다.

> # ref :link:

- [nvm github repo](https://github.com/nvm-sh/nvm)
