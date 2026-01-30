---
title: "[New ABAP] VALUE #( )"
excerpt: "VALUE #( )"

categories:
  - Newabap
tags:
  - [ABAP, "VALUE #"]

permalink: /newabap/value/

toc: true
toc_sticky: true

date: 2025-11-07
last_modified_at: 2025-11-07
---

## ✅ 'VALUE #'
<img src="/assets/images/posts_img/readme/value.png" alt="about_meee" width="40%" min-width="700px" itemprop="image">
     
### 개념
- 타입 추론(type inference) 을 통해, 변수의 선언된 타입에 맞게 초기값을 자동으로 생성한다.
- '#'은 컴파일러가 데이터 타입을 유추하도록 하는 기호
- '#'자리에 type ( 예를 들어, TY_S_DATA, LS_DATA, I, WERTV12 )이 들어갈 수도 있다.


### 목적
1. 코드 가독성 향상
2. 타입 명시 없이 안전하게 초기화
3. 내부 테이블/구조 초기 선언 시 편리


### 예시
<script src="https://gist.github.com/heyhyo-dev/cf584feca24bfc4af65b16eb755af9bb.js"></script>

### etc.
- 보통 BASE #, CORRESPONDING #, FOR IN 등과 같이 쓰인다.






























