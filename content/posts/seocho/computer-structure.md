---
title: 'Computer Structure'
date: 2024-05-13T05:32:52+09:00
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

![computer-structure](/assets/seocho/cumputer-structure.png)

# Today, I learned :grin:

## 1. CPU

### 1) ALU

Arithmetic(사칙연산)과 Logical(and, or, xor등 논리회로) 연산 유닛

### 2) CU

연결된 입출력장치와 통신하는 시스템 제어 유닛

### 3) Register

CPU의 일시적으로 저장하는 메모리 역할

- PC(Program Couter) : 메모리에서 가져올 (현재 or 다음) 명령어 주소를 일시적으로 저장
- IR(Instruction Register) : 메모리에서 가져온 명령어를 저장
- MAR (Memomry Address Register) : CPU가 데이터를 읽거나 쓰려는 메모리 주소를 일시적으로 저장
- MBR (Memory Buffer Register) : 메모리와 주고받을 데이터와 명령어 저장, 명령어는 IR로 전송되고 내용은 AR로 전송

## 2. Memory

> 메모리는 크게 kernel과 user 영역으로 나뉘고 kernel에는 OS, user에는 process가 적제됨

### 1) kernel

- 커널도 code, data, stack의 메모리 구조를 갖고 있음

### 2) code

- 프로그램 코드가 저장되는 영역으로 사용자가 작성한 프로그램 함수가 기계어로 저장됨
- 변경불가능 한 Read-only

### 3) data

- 프로그램의 전역 변수, 정적(static) 변수, 상수가 저장됨
- 프로그램 시작과 함께 할당되고, 종료될 때까지만 메모리에 존재

### 4) heap

- 사용자가 관리하는 영역
- 동적할당 변수들이 저장됨
- 메모리의 낮은 주소에서 높은 주소 뱡향으로 할당됨

### 5) stack

- 함수의 호출과 관계되는 지역변수와 매개변수가 일시적으로 저장됨
- 컴파일 타임에 의해 크기가 결정되므로 명시적으로 변수를 할당/해제할 필요가 없으며 호출이 완료되면 소멸함
- LIFO(Last In First Out)
- 커널 영역을 보호하기 위해 메모리의 높은 주소에서 낮은 주소 방향으로 할당됨
- stack의 영역에서 heap 영역을 침범하면 `stack overflow`, 반대는 `heap overflow`

# What I Want to More About :sob:

- 컴퓨터는 2진수로 연산을 하는데 VR까지 돌린다고 생각하면 반도체 처리속도가 얼마나 빠른걸까

- 오랫만에 이것 저것 찾아보며 해결하려고 하니 시간이 정말 오래걸린다. 그냥 네이버 블로그에 적을껄 그랬나? 차차 나아지겠지

# ref :link:

- [CPU 참조](https://velog.io/@jinny-l/CS-CPU의-구성-요소-레지스터-중심)

- [MEMORY 참조](https://codingwell.tistory.com/189)
