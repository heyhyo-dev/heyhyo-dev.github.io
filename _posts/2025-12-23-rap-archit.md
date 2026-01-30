---
title: "[RAP] 아키텍처(Architecture)"
excerpt: "아키텍처"

categories:
  - RAP
tags:
  - [RAP]

permalink: /rap/architecture/

toc: true
toc_sticky: true

date: 2025-12-23
last_modified_at: 2025-12-23
---

# BO(Business Object) 소개
> **BO(Business Object)란?**  
> 비즈니스 관점에서 “하나의 업무 단위”

e.g. Sales Order(판매오더): 헤더 + 아이템 + 스케줄라인 + 파트너 + 가격조건  
e.g. Purchase Order(구매오더): 헤더 + 아이템 + 납품일정 + 계정지정  

> **RAP를 BO 관점에서 설명한다면,**

"독립적으로 존재할 수 있는 비즈니스 데이터와 그 데이터를 다루는 모든 로직을 하나로 묶은 단위".   
1) 데이터 측면: 하나 이상의 CDS Entity가 트리(Tree) 계층 구조로 엮인 것.  
2) 로직 측면: 해당 데이터를 생성, 수정, 삭제(CRUD)하고 특정 상태로 변경(Action)하며 검증(Validation)하는 규칙의 집합.

&nbsp;

쉽게 비유하자면: 테이블이 '부품'이라면, **BO는 '완성된 자동차'**.  
자동차는 엔진(Header), 바퀴(Item), 옵션(Supplement) 등이 유기적으로 연결되어 있으며,  
'시동 걸기', '가속하기'와 같은 동작(Behavior)을 함께 가지고 있다.  

&nbsp;

> **BO 3대 구성 요소**
1. Data Model (CDS Entities): "무엇을 저장하는가?" (구조)  
2. Behavior Definition (BDEF): "무엇을 할 수 있는가?" (선언)  
3. Behavior Implementation (ABAP Class): "실제로 어떻게 돌아가는가?" (로직 구현)  

---

# RAP 3단계 아키텍처
<img width="2816" height="1536" alt="1766468074635" src="https://github.com/user-attachments/assets/22f8c4ac-0e01-4bb8-bd5c-b7f7686308ce" />

---

## 1. 데이터 모델링 (Data Modeling)
> 어떤 데이터를 사용할지 정의하고 UI에 맞게 가공하는 단계  

### a. BO(Business Object) 구성 요소
* `Root Entity` BO의 대표(헤더). 트랜잭션 중심점  
  * `Child Entity` Root에 종속되는 하위(아이템)  
* `Composition` “부모-자식 생명주기 동일” (부모 삭제 시 자식도 의미상 함께)  
* `Association` 엔티티 간 참조 관계(마스터데이터 참조 등)  
* `Cardinality` 1..1 / 0..* 같은 관계 수량 규칙  

### b. CDS 구현
* `Interface View` 내부 핵심 모델(재사용/정규화 중심). Composition/Association을 이곳에서 정의한다.  
* `Projection View` 외부 노출 모델(UI/API용으로 필드/구성 조정). 조회할 필드만 알맞게 구성한 View.
* `Annotation` CDS 엔티티/필드에 붙이는 “메타데이터(힌트/규칙/의미)”. 
  * @UI.lineItem : 이 필드로 리스트 컬럼 구성해  
  * @Semantics.amount.currencyCode: 'CurrencyCode' : 이 필드는 통화랑 묶어 해석해  
  * @ObjectModel.text.element: ['FieldText'] : 이 필드는 코드-텍스트 매핑하여 조회해  

---

## 2. 비즈니스 로직 정의 (Behavior & Business Logic)
> 데이터를 어떻게 조작(CRUD)할지, 어떤 제약 조건을 걸지 결정하는 단계

### a. BDEF(Behavior Definition) - 선언
이 엔티티(BO)가 어떤 트랜잭션/행위(CRUD, field control(readonly/mandatory), action, validation)를 지원하는지” 선언  
**Managed vs Unmanaged**  
`Managed` 저장(INSERT/UPDATE/DELETE)을 프레임워크가 수행  
`Unmanaged` 저장 로직을 개발자가 직접 구현(레거시/BAPI 연동 등)  

### b. Implementation Class - 구현
선언한 클래스 메소드에 실제 로직을 작성한다.  
* `Validation`: 저장 전 검증 (유효성 검사)
* `Determination`: 자동 계산/자동 채움  
* `Action`: approve/accept 같은 명령 처리 (펑션과 유사)
  * `Interface Action` 객체(인스턴스)를 선택해야 action 처리 가능
  * `Factory Action` 내가 선택한 객체를 카피하여 신규 키값으로 채번한 복사본
  * `Internal Action` 내부적으로 돌아가는 펑션 같은 역할

---

## 3. 서비스 노출 (Service Exposure)
> 작성된 로직을 외부(Fiori, Web API)에서 사용하도록 연결하는 단계  

### a. Service Definition
어떤 Projection Entity를 노출할지 선택한다.  

### b. Service Binding
통신 프로토콜(OData V4/V2) 및 용도(UI/Web API) 등의 Binding Type을 선택하여 실제로 호출 가능한 URL을 생성한다.  

---

## EML (ABAP에서 BO 조작 문법)
**Entity Manipulation Language**  
`정의` : ABAP 코드로 BO를 표준 방식으로 읽고/바꾸는 문법.  
`구문` : READ(엔티티 조회)/MODIFY(생성/수정/삭제/액션 실행)/COMMIT ENTITIES(트랜잭션 저장) 등을 사용한다.  
`IN LOCAL MODE`: 같은 트랜잭션(버퍼) 기준으로 읽기/쓰기.  
-> “DB에 커밋된 값”만 보는 게 아니라, EML로 수정해둔 버퍼(Transactional Buffer)까지 포함해서 읽겠다.  
-> 즉, MODIFY ENTITIES로 바꿔놓고 아직 COMMIT ENTITIES 전이어도, 같은 흐름 안에서 최신 상태를 읽고 싶을 때 씀.  
`결과 구조`: MAPPED / FAILED / REPORTED
* `MAPPED`: 새로 생성된 엔티티의 키 매핑 결과(%cid → 실제 키 등)  
* `FAILED`: 실패한 인스턴스 목록(어느 키가 왜 실패했는지)   
* `REPORTED`: 메시지(에러/경고/정보) 목록  
=> 꼭 셋 중 하나에는 값이 들어와야 에러가 안 난다!  


