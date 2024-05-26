---
title: '[TIL] Js [Quiz 0523] Destructuring'
date: 2024-05-27T06:19:18+09:00
weight: 1
# aliases: ["/first"]
categories: ["seocho"]
tags: ["에이블런", "서초구 4차 산업 소프트웨어 과정", "TIL", "Today I Learned", quiz]
author: "berry"
# author: ["Me", "You"] # multiple authors
showToc: true
TocOpen: false
draft: true            # want to draft : true
hidemeta: false
comments: false
description: "quiz0523"
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

```javascript
// 1. user 객체를 받아서 id와 name을 출력하는 함수를 3개의 함수로 작성하시오.
// (Function signature를 3개 이상으로 표현하기)
// 1) function f1(x,y){...}
// 2) var f1 = function(x,y){...}
// 3) const f3 = (x, y) => {}

// const f3 = (user) => `id=${user.id}, name=${user.name}`
console.log('----------------[1]----------------');

const hong = {id: 1, name: 'Hong'};
const lee = {id: 2, name: 'Lee'};
const kim = {id: 3, name: 'Kim'};

function f1(user) {
    console.log(user.id, user.name);
}
f1(hong);

const f2 = function(user){
    console.log(user.id, user.name);
}
f2(lee);

f3 = (user) => { console.log(user.id, user.name) };
f3(kim);


// 2. 다음 user 객체에서 passwd 프로퍼티를 제외한 데이터를 userInfo 라는 변수에 할당하시오.
console.log('----------------[2]----------------');

const user = {id: 1, name: 'Hong', passwd: 'xxx', addr: 'Seoul'}

const {id, name, addr} = user
const userInfo1 = { id, name, addr }
console.log(userInfo1);

let userInfo2 = (user) => {
    return {id, name, addr}
}
console.log(userInfo2(user));


// 3. 다음 arr에서 3개의 id를 id1, id2, id3로 할당하시오.
console.log('----------------[3]----------------');

const arr = [[{id: 1}], [{id:2}, {id: 3}]];
// cf. const id1 = arr[0][0].id;
const id1 = arr[0][0]['id'];
const id2 = arr[1][0]['id'];
const id3 = arr[1][1]['id'];

console.log(id1, id2, id3);
```

# Want to more about :sob:

- 2번을 한번에 처리하는 방법이 있으려나?


