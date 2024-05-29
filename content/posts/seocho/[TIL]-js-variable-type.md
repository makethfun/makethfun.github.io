---
title: '[TIL] Js Variable Type'
date: 2024-05-27T05:36:54+09:00
weight: 1
# aliases: ["/first"]
categories: ["seocho"]
tags: ["에이블런", "서초구 4차 산업 소프트웨어 과정", "TIL", "Today I Learned", "javascript", "variable"]
author: "berry"
# author: ["Me", "You"] # multiple authors
showToc: true
TocOpen: false
draft: true            # want to draft : true
hidemeta: false
comments: false
description: "variable type"
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
    Text: "JS의 변수타입" # edit text
    appendFilePath: true # to append file path to Edit link
---

# Today, I learned :grin:

![variable-type](https://www.imagevenue.com/ME18DWAB)

> JS의 원시타입은 stack, 참조타입은 heap에 저장됨

## 1. Primitive Type

-   각 변수들의 primitive value를 복사할 경우 데이터 값이 복사됨
-   변수 할당 시 메모리에 고정된 크기로 저장(Stack)
-   값에 대한 정의가 바뀌지 않는 **불변성(immutable)**
-   변수에 저장된 값(메모리)에 직접 접근할 수 있음
-   call by value
-   종류 : String, Number, Boolean, undefined, null, Symbol

-   Number : 32비트 안의 숫자값 SMI(Small Integer)는 stack에 저장, SMI 형식에 맞지 않는 숫자들은 heap에 저장

```javascript
// 할당 된 데이터 값을 복사함

let score = 100;

// 처음 x를 할당한 y의 값이 변하지 않음
let copy = x;

score = 80;
console.log(score); // 80
console.log(copy); // 100
```

## 2. Reference/Composite Type

-   각 변수들이 reference value를 복사할 경우 참조 주소값이 복사됨
-   변수 할당 시 메모리에 참조 주소값을 저장, 크기가 고정되어 있지 않음 (heap)
-   변수값이 저장된 메모리 주소값(포인터)을 가지고 있고, 자바스크립트 엔진이 메모리 주소를 이용하여 변수 값에 접근
-   call by reference

```javascript
let obj = { cnt: 100 };

let refOjb = obj;
obj.cnt = 80;

console.log(obj.cnt); // 80
console.log(refObj.cnt); // 80
```

## 3. typeof

해당 값의 종류를 알아보기 위해 typeof로 조회

```javascript
console.log(typeof 1); // number
console.log(typeof 'hello'); // string
console.log(typeof true); // boolean
console.log(typeof null); // **object
console.log(typeof undefined); // undefined
```

null은 결과값이 object 타입으로 나오므로 `====` 연산자를 사용하는게 더 확실하다.

# Want to more about :sob:

-   js에서 변수를 사용할 때 해당 타입을 생각하면서 코딩을 해야겠다.
-   현재 여러가지 실험들을 하고 있는데 정리하기가 너무 어렵다. 하지만 정리도 과정중 하나이기 때문에 포기하지말자.
-   한가지 혼동되는 건 variable table이라는 것이다. 강사님 설명에서는 이것이 stack에 자리잡고 있다고 했는데 primitive value와 refrenece의 포인터가 같이 들어가는 것인지? 헛갈린다.

# ref :link:

-   https://devowen.com/481
-   https://velog.io/@kero1004/javascript-%ED%83%80%EC%9E%85
