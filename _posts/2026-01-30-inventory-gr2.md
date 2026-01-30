---
title: "[MM/Inventory] 이동유형 입고 2편"
excerpt: "MM 입고 이동유형 알아보기 - Planned"

categories:
  - Inventory
tags:
  - [MM]

permalink: /inventory/gr2/

toc: true
toc_sticky: true

date: 2026-01-30
last_modified_at: 2026-01-30
---

# MIGO Goods Receipt 이동유형
<img width="1010" height="244" alt="image" src="https://github.com/user-attachments/assets/db03de7e-07ee-4f4a-9f40-4b3390361415" />  
Action(=Transaction) | 참조문서 | 이동유형  
위 3개로 MIGO 트랜잭션 처리가 진행된다.  
Action과 참조문서는 이동유형마다 다르게 설정한다.  

---

## <mark>With Reference</mark>
= Planned라고도 부른다. 참조문서로 입고 처리하는 이동유형들.   

### 101 입고
> A01 Goods Receipt |	R01 Purchase Order, R08 Order

GR goods receipt - 구매 오더 입고 혹은 생산 오더 입고  

&nbsp;

### 103 블락 재고로 입고
> A01 Goods Receipt | R01 Purchase Order

Goods receipt for purchase order into GR blocked stock  
**non-valuated로 입고되므로 회계문서(전표) 미생성**
물건은 왔지만, 전표는 안 끊음. 까다로운 검수가 끝나면 생성 가능.  
그게 아래 105번 이동유형.  

&nbsp;

### 105 릴리즈 블락 재고 - 가용 재고로 변경
> A05 Release GR blocked stock | R02 Material Document  

Release from GR blocked stock for purchase order  
**valuated로 회계문서 생성**  
blocked를 release하여 사용 가능 재고로 변경됨.  
회계문서 생성된다.

&nbsp;

### 103, 105 MMBE 흐름 전개
1) 구매 오더 - Z자재 100개 낸 상태  
<img width="668" height="87" alt="image" src="https://github.com/user-attachments/assets/d5b653d0-0583-490b-b97a-8e942e6afa55" />

2) 구매 오더 기준 103으로 Blocked 재고로 입고  
   : GR Blocked 재고로 100개 잡혀있다. 실질적으로 0001 창고까지 입고되지는 않았다.  
<img width="693" height="83" alt="image" src="https://github.com/user-attachments/assets/46052c08-ebd5-41f8-9cd6-3b6140d37a73" />

3) 103에서 생성된 자재문서를 참고문서로 하여 105 - Release한다.  
   : 드디어 가용재고로 0001 창고에 입고된다. 온오더스탁과 블락스탁 모두 사라진다.  
<img width="383" height="82" alt="image" src="https://github.com/user-attachments/assets/370e0b1b-3397-4fbc-981e-9908d7b3395d" />

&nbsp;

### 107, 109 ( 103, 105와 반대 )
107(valuated - 회계문서 생성) - 109(non-valuated - 회계문서 미생성)  
물건은 안 왔는데 전표부터 끊음 - 도착 확인만 함(전표 없음)  
e.g. 수입품, 고가의 설비  
보통 103, 105 선에서 처리한다.  

---








