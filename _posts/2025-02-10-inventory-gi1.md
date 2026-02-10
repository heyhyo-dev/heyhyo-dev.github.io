---
title: "[MM/Inventory] 이동유형 출고 1편"
excerpt: "MM 출고 이동유형 알아보기 - Unplanned"

categories:
  - Inventory
tags:
  - [MM]

permalink: /inventory/gi1/

toc: true
toc_sticky: true

date: 2026-02-10
last_modified_at: 2026-02-10
---

# MIGO Goods Issue 이동유형
<img width="563" height="129" alt="image" src="https://github.com/user-attachments/assets/f5218f3f-a3ed-4482-9ec6-6d4de3fd7dd3" />

Action(=Transaction) | 참조문서 | 이동유형  
위 3개로 MIGO 트랜잭션 처리가 진행된다.  
Action과 참조문서는 이동유형마다 다르게 설정한다.  

---

## <mark>Without Reference</mark>
= Unplanned라고도 부른다. 참조문서 없이 입고 처리하는 이동유형들.  
> 아래 이동유형들은 모두  
> A01 Goods Issue | R10 Other 로 처리한다.  
> 필수값 : 자재, 수량, 플랜트, 창고, ITEM OK 체크박스     

&nbsp;

### 331 Destructive Sampling  (331, 333, 335) 
검사를 위해 샘플을 파괴하는 것.  
e.g. 식품 맛보기, 자동차 충돌 테스트 등.  
**추가 필수값 : 코스트센터** -> 샘플로 뽑은 자재는 더 이상 재고 자산이 아니라 비용으로 처리. 누가 썼는지 적어야 하잖아!  
비용 발생 | 자산 감소 : 회계문서 생성됨.  
( 예외로, xx3이 가용재고에 해당한다. - 331:QI, 333: 가용, 335: 블락 )  
cf. Non-Destructive Sampling(321, 323, 325)은 액션 A08 Transfer Posting으로 처리된다. (전표 미생성)  

### 551 Scrapping (551, 553, 555)  
폐기 처리.  
e.g. 유효기간 경과, 파손 및 불량.  
비용 발생 | 자산 감소 : 회계문서 생성됨.  


&nbsp;

### 201 Cost Center Consumption
코스트센터 소비-> 자재 MRP뷰-additional data > consumption 탭에 사내에서 쓴 소비량 기록된다.  
**추가 필수값 : 코스트센터**  
비용 발생 | 자산 감소 : 회계문서 생성됨.  

&nbsp;

### 221 Project Consumption
프로젝트에서 자재 투입하기 위해 출고하는 것.  
**필수값 추가 - WBS Element(작업분할구조: 아파트 짓기 중 기초공사)**  

&nbsp;

### 241 Asset Consumption  
설비, 자산 수리 위해 부품 꺼낼 때.   
**필수값 추가 - Account Assignment 탭의 asset(자산 번호)**  

&nbsp;

---








