---
title: '[TIL] Js [Quiz 0522] Operating'
date: 2024-05-27T06:19:02+09:00
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
description: "quiz 0522"
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
// 1. for문을 이용하여 다음과 같이 정확한 숫자를 출력하는 코드를 작성하시오.
console.log('----------------[1]----------------');

for(let i = 0.1; i < 1; i = i + 0.1){
    if (i > 0.9) {
        console.log(1)
    } else { 
        console.log(Number(i.toFixed(1)));
    }
}

// 2. 1 ~ 10 사이의 정수에 대해 제곱근을 소숫점 3자리까지 출력하시오. 
console.log('----------------[2]----------------');

for(let i = 1; i < 11; i = i + 1){
    console.log(Number(Math.sqrt(i).toFixed(3)));
}

// 3. 오늘 날짜의 요일을 출력하는 switch문을 사용해서 작성해 보고, switch문을 사용하지 않은 더 간단한 방법도 찾아보세요.
console.log('----------------[3]----------------');

const today = new Date();
switch(today.getDay()){
    case 1: 
        console.log('오늘은 월요일 입니다.');
        break;
    case 2: 
        console.log('오늘은 화요일 입니다.');
        break;
    case 3: 
        console.log('오늘은 수요일 입니다.');
        break;
    case 4: 
        console.log('오늘은 목요일 입니다.');
        break;
    case 5: 
        console.log('오늘은 금요일 입니다.');
        break;
    case 6: 
        console.log('오늘은 토요일 입니다.');
        break;
    default: 
        console.log('오늘은 일요일 입니다.');
        break;
}

arr = ['월', '화', '수', '목', '금', '토', '일']
console.log(`오늘은 ${arr[today.getDay()-1]}요일 입니다.`);

// 4. 다음과 같이 올바른 더하기 연산을 하는 addPoints 함수를 작성하시오.
// (단, 소숫점 자리수는 긴쪽에 맞춘다)
console.log('----------------[4]----------------');

function compare (a, b){
    let str_a = a.toString().split('.')[1].length;
    let str_b = b.toString().split('.')[1].length;
    return str_a > str_b ? str_a : str_b;
}

function addPoints(a, b){
    return Number((a + b).toFixed(compare(a, b)));
}

console.log(addPoints(0.21354, 0.1));
console.log(addPoints(0.14, 0.28));
console.log(addPoints(0.34, 0.226));
```

# Want to more about :sob:

- Math library에 좀 더 편한 소수점 분리가 있지 않을까?

