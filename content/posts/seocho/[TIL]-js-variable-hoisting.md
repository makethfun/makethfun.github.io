---
title: '[TIL] Js Variable Hoisting'
date: 2024-05-21T09:51:55+09:00
# weight: 1
# aliases: ["/first"]
categories: ["seocho"]
tags: ["에이블런", "서초구 4차 산업 소프트웨어 과정", "TIL", "Today I Learned", "hoisting"]
author: "berry"
# author: ["Me", "You"] # multiple authors
showToc: true
TocOpen: false
draft: false            # want to draft : true
hidemeta: false
comments: false
description: "javascript hoisting"
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

# Today, I learned :grin:

## 1. var

함수의 코드 블록만을 스코프로 인정함. 함수 외부의 변수는 모두 전역변수가 되고 이는 변수의 중복 선언으로 의도치 않은 변수값 변경이 일어날 수 있음. 
이를 위해 let과 const를 도입.

대부분 언어는 block-level scope를 따르지만 자바스크립트는 function-level scope를 따름.
function-level scope : 함수 내에서 선언된 변수는 함수 내에서만 유효함. 함수 내부에서 선언된 변수는 지역변수이며 외부에서 선언된 변수는 모두 전역 변수이다.
block-level scope : 모든 코드블록(함수, if문, for문, while문, try/catch문 등) 내에서 선언된 변수는 코드 블록 내에서만 유효하고, 코드블록 외부에서 참조할 수 없음. 코드 블록 내부에서 선언한 변수는 지역변수이다.

```javascript
// function-level scope
// 전역변수로 만들어진 foo가 블록 내에서 만들어진 foo의 값을 참조함
var foo = 123; 
console.log(foo); // 123

{
  var foo = 456; // 전역변수
}
console.log(foo) // 456

// block-level scope
// 전역에서 블록 레벨 스코프 안에 만들어진 변수를 참조할 수 없음.
// 전역변수
let foo = 123; 

{
  let foo = 456; // 지역변수
  let bar = 456; // 지역변수
}

console.log(foo); // 123
console.log(bar); // ReferenceError: bar is not defined

```

## 2. 변수 중복 선언 금지

var는 동일한 이름을 갖는 변수 선언이 가능하지만 let은 SyntaxError가 발생함

```javascript
// 변수명 중복 가능
var foo = 123;
var foo = 456;

// 변수명 중복 불가: SyntaxError
let bar = 123;
let bar = 456; // Uncaught SyntaxError: Identifier 'bar' has already declared.
```

## 3. 호이스팅

호이스팅은 var 선언문이나 function 선언문 등을 해당 스코프의 선두로 옮긴 것처럼 동작하는 특성을 말한다. 하지만 var와는 달리 let으로 선언된 변수는 참조 에러(ReferenceError)가 발생한다. 이는 let으로 선언된 변수는 스코프의 시작에서 변수의 선언까지 일시적 사각지대(Temporal Dead Zone;TDZ)에 빠지기 때문이다.

```javascript
console.log(foo); // undefined
var foo;

console.log(bar); // Error: Uncaught ReferenceError: bar is not defined
let bar;
```

변수의 생성단계
- 선언 단계(Declaration phase): 변수를 실행컨텍스트의 변수객체(Variable Object)에 등록한다. 이 변수 객체는 스코프가 참조하는 대상이 된다.
- 초기화 단계(Initialization phase): 변수 객체(Variable Object)에 등록된 변수를 위한 공간을 메모리에 확보한다. 이 단계에서 변수는 undefined로 초기화된다.
- 할당 단계(Assginment phase): undefined로 초기화된 변수에 실제 값을 할당한다.

**var 키워드로 선언된 변수는 선언 단계와 초기화 단계가 한번에 이루어진다.** 즉, 스코프에 변수를 등록(선언 단계)하고 메모리에 변수를 위한 공간을 확보한 후, defined로 초기화(초기화 단계)한다. 따라서 변수 선언문 이전에 변수에 접근하여도 스코프에 변수가 존재하므로 에러가 발생하지 않고 undefined 를 반환한다. 이후 할당문에 도달하면 비로소 값이 할당된다. 이런 현상을 변수 호이스팅이라 한다.

```javascript
// 스코프의 선두에서 선언 단계와 초기화 단계가 실행된다.
console.log(foo); // undefined

var foo;
console.log(foo); // undefined

foo = 1; // 할당문에서 할당 실행
console.log(foo); // 1
```

**let 키워드로 선언된 변수는 선언 단계와 초기화 단계가 분리되어 진행된다.** 즉, 스코프에 변수를 등록(선언) 하지만 초기화 단계는 변수 선언문에 도달했을 때 이루어진다. 초기화 이전에 변수에 접근하려고 하면 참조 에러(ReferenceError)가 발생한다. 이는 메모리 공간이 아직 확보되지 않았기 때문이다. 따라서 스코프 시작 지점부터 초기화 시작 지점까지는 변수를 참조할 수 없다. 해당 구간을 *'일시적 사각지대(Temporal Dead Zone;TDZ)'* 이라고 부른다.

```javascript
// 스코프의 선두에서 선언 단계가 실행된다.
// 아직 변수가 초기화(메모리 공간 확보와 undefined로 초기화)되지 않아 변수를 참조할 수 없다.

console.log(foo); // ReferenceError: foo is not defined.

let foo; // 변수 선언문에서 초기화 단계가 실행된다.
console.log(foo); // undefined

foo = 1; // 할당문에서 할당 단계 실행된다.
console.log(foo); // 1
```

ES6에서는 호이스팅이 발생하지 않는 것과 차이가 없어보인다. 하지만 그렇지 않다.

```javascript
let foo = 1; // 전역변수

{
  cosnole.log(foo); // ReferenceError: foo is not defined
  let foo = 2; // 지역변수
}
```

위 예제의 경우, 전역 변수 foo 값이 출력될 것 같지만 호이스팅이 발생하므로 ReferenceError가 발생한다. 


# Want to more about :sob:

- 과거 hoisting을 통해 코딩 방식을 함수를 한군데 모아두고 실행시 불러올 수 있었다. 해당 방식은 다른 사람이 코드를 리뷰하기 쉬워진다. 다만 변수명이 중복될 때나 runtime 오류가 발생했을 때 해당 오류를 찾아내기 어렵다.
- 예제를 찾다보니 ref 사이트를 많이 참조했다. 
- 글쓰기 구조화가 필요한거 같다. index가 엉망이다.
- 이미지 파일을 등록할 서버를 찾아야겠다.

# ref :link:

- https://poiemaweb.com/es6-block-scope