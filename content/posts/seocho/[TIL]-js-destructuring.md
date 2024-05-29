---
title: '[TIL] Js Destructuring'
date: 2024-05-29T17:18:21+09:00
# weight: 1
# aliases: ["/first"]
categories: ["seocho"]
tags: ["에이블런", "서초구 4차 산업 소프트웨어 과정", "TIL", "Today I Learned"]
author: "berry"
# author: ["Me", "You"] # multiple authors
showToc: true
TocOpen: false
draft: false            # want to draft : true
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

# Today, I learned :grin:

## 1. 구조 분해 할당 (destructuring) 개요

> 배열이나 객체의 속성을 해체하여 그 값을 개별 변수에 담을 수 있도록 하는 Javascript Expression

### 1) 일반적인 할당문과 구조분해문법

#### 기본사용법

좌변에 변수 하나, 우변에 데이터(number, string, array, object...) 하나를 써서 데이터를 변수에 1:1로 할당함

```javascript
let x = 10;
let xArr = [10, 20, 30];
```

좌변에 할당하고자 하는 변수, 우변에 데이터(array, object...)를 써서 데이터의 속성을 다:1로 할당함

```javascript
let [xArr1, xArr2] = xArr;
console.log(xArr1); // 10
console.log(xArr2); // 20
```

변수에 기본값을 할당하려면 해당 값이 선언된 후 undefined 였을 때 사용함

```javascript
let a, b;

[a = 5, b = 7] = [1];
console.log(a); // 1
console.log(b); // 7
```

#### 변수값 교환하기

일반적으로 두 변수를 교환하려면 임시 변수가 필요하지만 destructuring은 바로 교환 가능

```javascript
let a = 1;
let b = 3;

[a, b] = [b, a];
console.log(a); // 3
console.log(b); // 1
```

함수의 return 배열 값도 구조분해로 각각 변수로 사용 가능

```javascript
function f() {
    return [1, 2];
}

var a, b;
[a, b] = f();
console.log(a); // 1
console.log(b); // 2
```

#### 반환 값 무시하기

일부 반환 값이나 전부를 무시할 수 있음

```javascript

```

#### 변수에 배열 나머지 할당하기

`...rest`를 이용하여 나머지 변수들을 한꺼번에 할당할 수 있음

```javascript
const { a, ...others } = { a: 1, b: 2, c: 3 };
console.log(others); // { b: 2, c: 3 }

const [first, ...others2] = [1, 2, 3];
console.log(others2); // [2, 3]
```

## 2. 구조분해할당 종류

### 1) Object Destructuring

```javascript
const { id, name } = { id: 1, name: 'Hong' };
console.log(id, name);

const user = {
    id: 1,
    name: 'Hong',
    addr: {
        city: 'Seoul',
        road: '길',
    },
};
```

#### 변수명 변경

```javascript
// const { id: userId, name: userName } = user;
// console.log("🚀 ~ userId, userName :", userId, userName);
```

#### 객체 속에 있는 값을 변수로 만들기

```javascript
// 해당 과정
const { id, addr } = user;
console.log(id, addr); // 1 { city: 'Seoul', road: '길' }

const { city } = addr;
console.log(city); // Seoul

// 한번에 가져오기
const {
    id,
    addr: { city },
} = user;
console.log(city); // Seoul

// 키값 변경해서 가져오기
const {
    id,
    addr: { city: addrCity },
} = user;
console.log(addrCity); // Seoul

// 조건문으로 값 가져오기
const mainField = user.id > 5 ? 'name' : 'addr';
const { [mainField]: target } = user;
console.log(target); // { city: 'Seoul', road: '길' }
```

#### 참조값과 생성값

```javascript
user = {
    id: 1,
    addr: {
        city: 'S',
        road: 'X',
    },
};

x = user;
y = { ...user };
z = { ...user, addr: { ...user.addr } };
console.log(x, y, z);

user.addr.city = 'P';
console.log(x.addr.city);
console.log(y.addr.city);
console.log(z.addr.city); // x, y는 user의 참조값, z는 생성값?
```

### 2) Array/Iterator Destructuring

#### 배열 값 가져오기

```javascript
const arr = [1, 2, 3, 4, 5]; // { 0: 1, 1: 2... }
const { 1: x1, 3: x2 } = arr;
console.log(x1, x2); // 2 4

const [a, b] = [1, 2];
console.log(a, b); // 1 2

const [, , e] = [1, 2, 3];
console.log(e); // 3

const arr = [123, 456];

let [aa, bb] = arr;
let { 0: aa, 1: bb } = { ...arr }; // spread

const users = [
    { id: 1, name: 'Hong' },
    { id: 2, name: 'Kim' },
    { id: 3, name: 'Lee' },
];

// 배열 안 객체 값 가져오기
const [, { id: userId }] = users;
console.log(userId); // 2
```

### 3) Default Value Destructuring

#### 없는 요소들은 변수로 생성

```javascript
const { id, name, addr = 'Seoul' } = { id: 1, name: 'Hong', add: 'Pusan' };
console.log('🚀 ~ :', id, name, addr);
const [a, b, c = 3] = [1, 2];
console.log('🚀 ~ a, b, c:', a, b, c);

const [user] = users;
console.log(user);
```

// 이미 할당된 값은 변경 불가?

```javascript
const { id, nick = 'Hong' } = { id: 1, nick: '' };
console.log(id, nick); // undefined

const { id, nick = 'Hong' } = { id: 1, nick: 'Kim' };
console.log(id, nick); // 'kim'

const [e, f, g = 3] = [1, 2, 0];
console.log(e, f, g); // 0
```

// undefined로 된 값은 변경될 수 있음

```js
const { id, nick = 'Hong' } = { id: 1, nick: undefined };
console.log(id, nick);

const [ e, f, g = 3 ] = [ 1, 2, undefined ];
console.log(e, f, g);

// n is not defined ????
const obj = { i: 1, j: 2, l: 3, m: 4, n: 5 };
const { i, j, l } = obj;
console.log(i, j, l);

let { j, i, k = i * j * n } = obj; // ** n은 할당되지 않아서 Error
const { k = i \* 10, i, j } = obj;
console.log(k);
console.log(j, i, k);

let q, s, r;
({ r = q \* 10, q, s } = { q: 10, s: 20 });
console.log(q, s, r); // r은 q가 할당 전이라 NaN이 됨?
```

### 4) rest 연산자

```js
const arr = [1, 2, 3, 4, 5];
const [a1, a2, ...rest] = arr;
console.log(a1, a2, rest);

const { l, m, ...restObj } = obj;
console.log(l, m, restObj);
```

### 5) Arguments Destructuring

```js
const user = {
    id: 1,
    name: 'Hong',
    addr: {
        city: 'Seoul',
    },
};

function fn(arg1, { id, name }, arg2) {
    console.log(arg1, id, name, arg2);
}

fn(10, user, 20);

const [arg1, { id, name }, arg2] = [10, user, 20];
console.log(arg1, id, name, arg2);

let un;
const [a] = un; // un is not iterable
const [a] = un || [];
const a = un?.[0];
console.log(a);

const { name: n, age = 30 } = { name: 'Lee' };
console.log(n, age); // Lee
```

#### 기존 할당된 값은 새로 변하지 않음

```js
const { age2 = 30 } = { name: 'Park', age2: 20 };
console.log(age2); // 20

const { age2: age3 = 33 } = { age22: 20 };
console.log(age2);
console.log(age3);

const u3 = {
    id: 3,
    name: 'kim',
    addr: {
        id: 1,
        city: 'Seoul',
    },
};

let {
    id: idd,
    addr: { id: aid },
} = u3;
console.log(idd, aid);

const arr = [1, 2, [3, 4], [5, 6], { ax: 7, ay: 8 }, { ax: 9 }];
const [, x, [, y], z, , { ax }] = arr;
console.log(x, y, z, ax);

const { 1: p, 4: q } = arr;
console.log(p, q);

const [, , , , { ay: a1 }, { ax: a2 }] = arr;
console.log(a1, a2);

const [k, v] = Object.entries(user);
console.log(k, v);

const kim = { nid: 3, nm: 'Hong', addr: 'Pusan' };

const newKim = { ...kim };

const newObj = {};
function copyObject(obj) {
    for (const k in obj) newObj[k] = obj[k];
    return newObj;
}

// copyObject(kim)

const newKim = copyObject(kim); // shallow copy
console.log(newKim);
newKim.addr = 'Daegu';
console.log(kim.addr !== newKim.addr);
```

### 6) Class Destructuring

#### class의 constructor를 변수로 뺄 수 있음

```js
class A {
    constructor(a, b) {
        this.a = a;
        this.b = b;
    }
}
const x = new A(1, 2);
const { a, b } = x;
console.log('🚀 ~ a, b:', a, b);
```

# Want to more about :sob:

-   배열이나 객체같은 iterable 객체에서 값을 뽑아낼 때 유용할 것 같다.
-   반복문을 돌릴 때 조건 안에서도 사용 가능하다.
-   사례는 많으니 틈틈히 연습해야 할 것 같다.

# ref :link:

-   [MDN](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Operators/Destructuring_assignment)
-   [비구조화할당](https://learnjs.vlpt.us/useful/06-destructuring.html)
