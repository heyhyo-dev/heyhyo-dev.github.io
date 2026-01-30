---
title: "[MM] Inventory_이동유형 입고 1편"
excerpt: "MM 입고 이동유형 알아보기 - Unplanned"

categories:
  - Inventory
tags:
  - [MM]

permalink: /inventory/gr/

toc: true
toc_sticky: true

date: 2026-01-28
last_modified_at: 2026-01-28
---

# MIGO Goods Receipt 이동유형
<img width="1010" height="244" alt="image" src="https://github.com/user-attachments/assets/db03de7e-07ee-4f4a-9f40-4b3390361415" />  
Action(=Transaction) | 참조문서 | 이동유형  
위 3개로 MIGO 트랜잭션 처리가 진행된다.  
Action과 참조문서는 이동유형마다 다르게 설정한다.  

---

## <mark>Without Reference</mark>
= Unplanned라고도 부른다. 참조문서 없이 입고 처리하는 이동유형들.  
> 아래 이동유형들은 모두  
> A01 Goods Receipt | R10 Other 로 처리한다.  
> 필수값 : 자재, 수량, 플랜트, 창고, ITEM OK 체크박스  
> XX1 : 가용재고, XX3 : QI재고, XX5 : Blocked재고    

### 561 기초재고  (561, 563, 565)  
Initial entry of stock balances into unrestricted-use stock (기초 재고 초기 입고)  

### 501 Without PO (501, 503, 505)  
Receipt w/o purchase order into unrestricted-use stock (구매 오더 없는 입고)  

> 501 vs. 561  
> 561: 기존 시스템(Legacy)에 있던 재고 데이터를 SAP로 데이터 마이그레이션, 첫 오픈 시점.  
> 501: 시스템 운영 중에 구매 부서의 정식 발주(PO) 없이 외부에서 물건이 들어왔을 때.  

### 511 무상입고
Receipt of delivery without charge (무상입고)
**추가 필수값 : 벤더, 텍스트**  

### 521 Without Prod.Order (521, 523, 525)  
Receipt w/o production order into unrestr.-use stock (생산 오더 없는 입고)

### 531 부산물 ( By-Product )  
Receipt of by-product into unrestricted-use stock (부산물 입고)  
주산품(Main Product)을 만들다가 **부수적으로 튀어나온 찌꺼기인데 돈이 되는 것(부산물)**을 입고 잡을 때  
e.g. 정유 공장: 휘발유(Main) 뽑고 남은 아스팔트(By-product) 입고.  

### 451 반품 from Customer 
Customer returns (고객 반품)  
고객이 반품한 물건을 MM 모듈에서 직접 잡을 때. (SD 모듈의 Delivery 없이)  
**추가 필수값 : Customer**
이 재고는 **'가용 재고(Unrestricted)'**가 아니라 **'반품 재고(Returns)'**로 잡힌다.  
나중에 453번을 써서 가용 재고로 풀어줘야 사용할 수 있다.

---









