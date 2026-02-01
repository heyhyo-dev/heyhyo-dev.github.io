---
title: "[MM/Inventory] 이동유형 입고 3편"
excerpt: "MM 입고 이동유형 알아보기 - Return/Cancel"

categories:
  - Inventory
tags:
  - [MM]

permalink: /inventory/gr3/

toc: true
toc_sticky: true

date: 2026-02-01
last_modified_at: 2026-02-01
---

# MIGO Goods Receipt 이동유형
<img width="1010" height="244" alt="image" src="https://github.com/user-attachments/assets/db03de7e-07ee-4f4a-9f40-4b3390361415" />  
Action(=Transaction) | 참조문서 | 이동유형  
위 3개로 MIGO 트랜잭션 처리가 진행된다.  
Action과 참조문서는 이동유형마다 다르게 설정한다.  

---

## <mark>Return</mark>

### 122 일반반품
> A02 Return Delivery |	R02 Material Document

입고 101의 반품 이동유형으로, **Reason for Movement** 필수로 입력해야 함.  
<img width="850" height="302" alt="image" src="https://github.com/user-attachments/assets/924141d8-d525-4de4-9b20-4b5fd97d1aeb" />
가용재고가 온오더스탁으로 이동한다.  
정상입고로 창고에 넣었는데 반품하는 경우 ( 우리 창고 재고 줄고, 회계적으로도 다시 돈 받을 권리 생김)  

&nbsp;

### 124 입고보류반품
> A02 Return Delivery |	R02 Material Document

Blocked 103의 반품 이동유형으로, **Reason for Movement** 필수로 입력해야 함.  
GR Blocked Stock이 감소한다.  
입고 보류 상태에서 반품. ( 애초에 우리 자산으로 잡은 적 없으니 회계전표 없이 수량만 정리)  

&nbsp;

### 101, 103 후속납품처리
> A06 Subsequent Delivery |	R02 Material Document

취소하고 재입고 처리할 때 사용된다.  
122, 124에 따라 자동으로 101, 103으로 채워져 처리된다.  

&nbsp;

### 161 Return for Purchase Order
> A01 Goods Receipt | R01 Purchase Order

PO 생성 시 return 체크박스 체크, GR 시 자동으로 161로 출고 처리 & 벤더에게 받을 돈(credit memo) 생성.  
처음부터 반품을 목적으로 거래. e.g. 맥주병 반납하고 보증금 돌려받는 경우.  

&nbsp;

---
## <mark>Cancellation</mark>( reversal로 기존 번호 +1 )

### 102 입고취소, 123(반품취소) ...
> A03 Cancellation |	R02 Material Document

해당 문서번호 입력 시 자동으로 이동유형 잡혀서 처리된다.  

---




