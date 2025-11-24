---
title: "[New ABAP] FOR ... IN "
excerpt: "FOR IN 구문"

categories:
  - SAP ABAP
tags:
  - [ABAP, FOR IN]

permalink: /sap-abap/forin/

toc: true
toc_sticky: true

date: 2025-11-24
last_modified_at: 2025-11-24
---

## ✅ FOR wa IN ...
<img width="1536" height="1024" alt="image" src="https://github.com/user-attachments/assets/521a6eb9-7dba-40b7-943d-ca5b23d63272" />


### 개념
- 기존 LOOP AT 구문과 흡사하다.
- 내부 테이블을 순회(iteration) 하여 새로운 값(구조, 테이블, 필드, 문자열 등)을 생성하는 표현식 기반 반복문
- VALUE, COND, REDUCE 등과 함께 사용된다.  
&nbsp;
&nbsp;

### 기본 문법
1. 내부 테이블 순회  
```abap
FOR wa IN it_table
```

2. 조건 필터링
```abap
FOR wa IN it_table WHERE ( condition )
```

3. 인덱스 기반
```abap
FOR idx = 1 WHILE idx <= 10
```  
&nbsp;
&nbsp;

### 예시 1
**BEFORE**  
```abap
  LOOP AT LT_SELECT INTO DATA(LS_SELECT).

    APPEND LS_SELECT TO LT_FILE.

  ENDLOOP.
  
  LT_TABLE = CORRESPONDING #( LT_FILE ).
```  
&nbsp;

**AFTER 1**  
```abap
  LT_FILE = VALUE #( BASE LT_FILE FOR LS_SELECT IN LT_SELECT
                   ( LS_SELECT ) ).
                   
  LT_TABLE = CORRESPONDING #( LT_FILE ). 
```  
&nbsp;

**AFTER 2**  
```abap
LT_TABLE = VALUE #( BASE LT_TABLE FOR LS_SELECT IN LT_SELECT
                   ( CORRESPONDING #( LS_SELECT ) ) ).
```  
&nbsp;
&nbsp;

### 예시 2
**BEFORE**  
```abap
  LOOP AT LT_SELECT INTO DATA(LS_SELECT).

    LOOP AT GT_TR INTO DATA(LS_TR) WHERE BUKRS          = LS_SELECT-BUKRS
                                     AND BUKRS_VBUND    = LS_SELECT-BUKRS_VBUND
                                     AND ACCOUNT_PERIOD = LS_SELECT-ACCOUNT_PERIOD.
      IF SY-SUBRC <> 0.
        CONTINUE.
      ENDIF.

      MOVE-CORRESPONDING LS_TR TO LS_TABLE.
      APPEND LS_TABLE TO LT_TABLE.
      CLEAR  LS_TABLE.

    ENDLOOP.
  ENDLOOP.
```
&nbsp;

**AFTER**  
```abap
  LT_TABLE = VALUE #( BASE LT_TABLE FOR LS_SELECT IN LT_SELECT
                                    FOR LS_TR     IN GT_TR    WHERE ( BUKRS          = LS_SELECT-BUKRS
                                                                AND   BUKRS_VBUND    = LS_SELECT-BUKRS_VBUND
                                                                AND   ACCOUNT_PERIOD = LS_SELECT-ACCOUNT_PERIOD )
                        ( CORRESPONDING #( LS_TR ) ) ).
```
> 이중 LOOP도 FOR IN으로 간결하게 가능하다.  
> APPEND 할 필요 없이 알아서 된다.

