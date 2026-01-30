---
title: "[MM/Overview] 기준 정보 (Master Data)"
excerpt: "MM Master Data 알아보기"

categories:
  - MM_Overview
tags:
  - [MM]

permalink: /mmview/master/

toc: true
toc_sticky: true

date: 2025-11-20
last_modified_at: 2025-11-20
---

# MM 기준 정보
>**기준 정보란 무엇인가.** <br/>
>업무 처리(Transaction)를 위한 기준/근간이 되는 정보 <br/>
>표준화를 목적으로 프로세스를 통제하고 기본값을 제시한다. 

---
## 자재 마스터 (Material Master)
자재(원자재, 반제품, 완제품 등)에 대한 모든 정보를 저장한 대표 마스터데이터.

생성 T-CODE `MM01`

---
## 공급업체 마스터 (Vender Master=BP)
>ECC까지는 공급업체/고객 마스터가 별도 관리되었으나, <br/> S/4HANA부터는 BP로 통합 관리한다.

공급업체 정보(주소, 조달조건, 지급조건 등)를 관리하는 데이터.

조직 레벨이 두 가지로 구성됨
* General Data (공통)
* Company Code Data (회계)
* Purchasing Data (구매)  
-> FI와 MM에서 함께 사용됨


생성 T-CODE `XK01` / `BP`

---
## 구매정보 레코드 (Info Record)
특정 자재 + 특정 공급업체 조합에 대한 구매 조건 정보를 저장하는 데이터.

생성 T-CODE `ME11`

---
## 소스 리스트 (Source List)
자재를 어떤 공급업체로부터 구매할 수 있는지 정의하는 리스트.

생성 T-CODE `ME01`
