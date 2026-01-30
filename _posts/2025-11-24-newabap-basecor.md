---
title: "[New ABAP] BASE/CORRESPONDING #"
excerpt: "BASE/CORRESPONDING #"

categories:
  - NewABAP
tags:
  - [ABAP, BASE, CORRESPONDING]

permalink: /newabap/basecor/

toc: true
toc_sticky: true

date: 2025-11-24
last_modified_at: 2025-11-24
---

<img width="1536" height="1024" alt="image" src="https://github.com/user-attachments/assets/35393e8e-fb00-4ad5-b54e-82c6134787ac" />

## ✅ BASE

### 개념
- 기존 테이블의 내용을 유지하면서 새 항목을 추가하는 데 사용되는 구문
- 변수 타입이 서로 맞아야 한다.


### BASE 예시 1
**BEFORE**  
```abap
    LS_DISP-VKBUR       = LS_TMP-VKBUR.       "부서
    LS_DISP-VKBUR_NM    = LS_TMP-VKBUR_NM.    "부서명
    LS_DISP-WAERK       = LS_TMP-WAERK.       "통화
    LS_DISP-MEINS       = LS_TMP-MEINS.       "단위

    APPEND LS_DISP TO GT_DISP.
    CLEAR  LS_DISP.
```

**AFTER**  
```abap
GT_DISP = VALUE #( BASE GT_DISP 
                 ( VKBUR       = LS_TMP-VKBUR    
                   VKBUR_NM    = LS_TMP-VKBUR_NM 
                   WAERK       = LS_TMP-WAERK    
                   MEINS       = LS_TMP-MEINS  ) ).
```

### BASE 예시 2
```abap
TYPES: BEGIN OF ty_person,
         id   TYPE i,
         name TYPE string,
         age  TYPE i,
       END OF ty_person.

DATA(ls_person) = VALUE ty_person(
    id = 1
    name = 'Kim'
    age = 30
).

" 나이를 31로 변경한 새로운 구조 생성
DATA(ls_updated) = VALUE ty_person(
    BASE ls_person
    age = 31
).
```
>결과: id = 1 / name = Kim / age = 31 (나머지는 기존 값 유지)

---

## ✅ CORRESPONDING #

### 개념
- 흔히 알고 있는 CORRESPONDING의 개념이다. 동일한 이름을 가진 필드만 자동으로 매핑한다. 

### CORRESPONDING # 예시 1
```abap
TYPES: BEGIN OF ty_src,
         id   TYPE i,
         name TYPE string,
         desc TYPE string,
       END OF ty_src.

TYPES: BEGIN OF ty_tgt,
         id   TYPE i,
         name TYPE string,
         note TYPE string, " src에 없는 필드
       END OF ty_tgt.

DATA(ls_src) = VALUE ty_src( id = 10 name = 'SAP' desc = 'desc...' ).

" 대상 타입을 명시적으로 선언한 뒤, CORRESPONDING # 으로 자동 매핑
DATA(ls_tgt) = CORRESPONDING #( ls_src ).
```
>결과: ls_tgt-id = 10, ls_tgt-name = 'SAP', ls_tgt-note = initial   
>ls_src의 id, name이 ls_tgt의 같은 이름 컴포넌트로 복사된다.  
>desc는 ls_tgt에 없으므로 무시된다.  
>note는 ls_src에 없으므로 초기값을 유지한다.  


















