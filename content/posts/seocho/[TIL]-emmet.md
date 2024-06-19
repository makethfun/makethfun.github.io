---
title: '[TIL] Emmet'
date: 2024-06-19T16:53:42+09:00
weight: 1
# aliases: ["/first"]
categories: ["seocho"]
tags: ["에이블런", "서초구 4차 산업 소프트웨어 과정", "TIL", "Today I Learned"]
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

# Emmet 문법

## 1. `html:5` 생성

```bash
# html 생성 명령어
html:5
```

## 2. 구조화하기

### 1) 자식요소 `>`

a. `>`를 사용하여 자식요소 생성

```bash
# div 안의 ul 안의 li
div>ul>li
```

b. 결과

```html
<div>
    <ul>
        <li></li>
        <ul>
            <div></div>
        </ul>
    </ul>
</div>
```

### 2) 형제요소 `+`

a. `+`를 사용하여 형제요소 생성 - 같은 단계의 태그

```bash
# div, p, bq 태그 생성
div+p+bq
```

b. 결과

```html
<div></div>
<p></p>
<blockquote></blockquote>
```

### 3) 한단계 위 `^`

a. `^`를 사용하여 한단계 위 태그 생성

```bash
# div 두개 만들고 안에 p와 bq태그 생성, p 안에 span과 em태그 만들기
div+div>p>span+em^bq
```

b. 결과

```html
<div></div>
<div>
    <p>
        <span></span>
        <em></em>
    </p>
    <blockquote></blockquote>
</div>
```

## 3. 태그 연산

### 1) 갯수 만큼 만들기 `*`

a. `*`를 사용하여 갯수 만큼 태그 만들기

```bash
# ul 안에 li태그 5개 만들기
ul>li*5
```

b. 결과

```html
<ul>
    <li></li>
    <li></li>
    <li></li>
    <li></li>
    <li></li>
</ul>
```

### 2) 그룹 `()`

a. `()`를 사용하여 태그끼리 묶기

```bash
# div안에 header와 footer를 만들고 header안에 ul, li 2개, a태그, ㄹooter 안에 p 태그만들기
div>(header>ul>li*2>a)+footer>p
```

b. 결과

```html
<div>
    <header>
        <ul>
            <li><a href=""></a></li>
            <li><a href=""></a></li>
        </ul>
    </header>
    <footer>
        <p></p>
    </footer>
</div>
```

## 3. 속성 - attribute

### 1) id, class 태그 `#`, `.`

a. `#`를 사용하여 id, `.`을 사용하여 class 만들기

```bash
# id가 header인 div, class가 page인 div, id가 footer이고 class가 class1, 2, 3인 div만들기
div#header+div.page+div#footer.class1.class2.class3
```

b. 결과

```html
<div id="header"></div>
<div class="page"></div>
<div id="footer" class="class1 class2 class3"></div>
```

### 2) custom 속성 만들기 `[]`

a. `[]`를 사용하여 속성 만들어주기

```bash
# title이 hellow world, colspan이 3인 td 만들기
td[title="Hello world!" colspan=3]

# 속성이름만 명시해줘도 됨
td[colspan title]
```

b. 결과

```html
<td title="Hello world!" colspan="3"></td>
<td colspan="" title=""></td>
```

### 3) 아이템 넘버링과 순서, 시작값

-   넘버링 `$`
-   순서 `@`, 역순 `@-`
-   시작값 `@<number>`

a. `$`를 사용하여 넘버링 / `@-<number>` 시작값과 역순 넘버링

```bash
# ul안에 item을 클래스로 갖는 리스트 5개 생성
ul>li.item$*5

# ul안에 item을 클래스로 갖고, 클래스명 3부터 4개 역순으로 생성
ul>li.item$@-3*4
```

b. 결과

```html
<!-- ul안에 item을 클래스로 갖는 리스트 5개 생성 -->
<ul>
    <li class="item1"></li>
    <li class="item2"></li>
    <li class="item3"></li>
    <li class="item4"></li>
    <li class="item5"></li>
</ul>

<!-- ul안에 item을 클래스로 갖고, 클래스명 3부터 4개 역순으로 생성 -->
<ul>
    <li class="item6"></li>
    <li class="item5"></li>
    <li class="item4"></li>
    <li class="item3"></li>
</ul>
```

### 4) elements에 text넣기 `{}`

a. `{}`를 사용하여 elements에 텍스트 추가

```bash
# p태그 안에 Click 텍스트 아래 a 태그 안에 here 텍스트, to continue 텍스트
p>{Click}+a{here}+{to continue}
```

b. 결과

```html
<p>Click<a href="">here</a>to continue</p>
```

> # Want to more about :sob:

> # ref :link:

-   [emmet syntax](https://docs.emmet.io/abbreviations/syntax/)
