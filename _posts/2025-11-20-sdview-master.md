---
title: "[SD/Overview] 기준 정보 (Master Data)"
excerpt: "SD Master Data 알아보기"

categories:
  - SD_Overview
tags:
  - [SD]

permalink: /sdview/master/

toc: true
toc_sticky: true

date: 2025-11-20
last_modified_at: 2025-11-20
---

# SD 기준 정보
>**기준 정보란 무엇인가.** <br/>
>업무 처리(Transaction)를 위한 기준/근간이 되는 정보 <br/>
>표준화를 목적으로 프로세스를 통제하고 기본값을 제시한다. 

---
## 자재 마스터 (Material Master)
Sales에 집중하여 영업 문서 생성 시 가격 결정 등과 같은 데이터를 관리한다. 

**자재 마스터 생성 시 SD 모듈에서 핵심 뷰**  
Sales: Sales Org Data 1  
Sales: Sales Org Data 2  
Sales: General / Plant Data  


생성 T-CODE `MM01`

---
## 고객 마스터 (Customer Master=BP)
>ECC까지는 공급업체/고객 마스터가 별도 관리되었으나, <br/> S/4HANA부터는 BP로 통합 관리한다.

판매 활동을 위해 필요한 고객 정보를 저장하는 SD의 가장 핵심 마스터데이터.  

일반 데이터 / 회사코드 데이터 / 판매영역 데이터 로 구분된다.  

고객을 기능별로 다음과 같이 정의한다.  
1. 판매처(SP) : Sold-To Party  
2. 납품처(SH) : Ship-To Party  
3. 청구처(BP) : Bill-To Party  
4. 지급인(PY) : Payer  


생성 T-CODE `XD01 / VD01` / `BP`

---
## 고객-자재 정보 레코드 (Customer-Material Info Record)
특정 자재 + 특정 고객 조합에 대한 구매 조건 정보를 저장하는 데이터.  
 
>예시: 현대차가 제네시스 1대 만드는 데 부품이 필요해서 업체에 소요량을 갖다준다.  
>현대차 왈, "우리 A부품 100개 주라."  
>업체 왈, "우리는 그거 A부품이 아니라 B부품이라고 부르는데?"  
>이 경우, 이름을 변환하여 매핑하는 것이 고객 자재 정보다.


생성 T-CODE `VD51`

---
## 가격 마스터 (Condition Master)
가격결정을 위해 필요한 조건금액/할인/세금 등을 관리하는 마스터데이터.  
제품별, 고객별로 적용되는 금액을 관리한다.


생성 T-CODE `VK11`
