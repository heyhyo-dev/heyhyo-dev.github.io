---
title: "[SD/Overview] 조직"
excerpt: "SD 조직 알아보기"

categories:
  - SD_Overview
tags:
  - [SD]

permalink: /sdview/org/

toc: true
toc_sticky: true

date: 2025-11-20
last_modified_at: 2025-11-20
---

# SD 조직 구조
<img width="796" height="378" alt="image" src="https://github.com/user-attachments/assets/6b866760-9a51-4ade-905d-9d12a948d313" />


## <mark>Client</mark>
서버 안의 여러 방

## <mark>Company Code</mark>
독립적 재무제표를 만들어낼 수 있는 최소 단위 <br/>
Client와 1:N 관계

## <mark>Plant</mark>
공장 <br/>
Company Code와 1:N 관계

## <mark>Storage Location</mark>
창고 : 재고실사와 같이 자재를 보관하고 관리한다. <br/>
Plant와 1:N 관계

## <mark>Shipping Point</mark>
출하지점  
하나의 출하지점에서 복수의 Plant의 제품 출하도 가능하다. 

## <mark>Sales Area</mark>
영업 영역  
마스터 생성 및 영업 문서 생성 등에서 반드시 선택해야 하는 조직  
하나의 Sales Area는 반드시 하나의 Company Code에만 할당 가능하다.  
영업 조직과 유통경로는 Plant와 N:N 관계

### <mark>Sales Organization</mark>
영업조직  

### <mark>Distribution Channel</mark>
유통경로  

### <mark>Division</mark>
제품군  


## <mark>Sales Office</mark>
사업장  

## <mark>Sales Group</mark>
영업 그룹  




## 예시 조직도 살펴보기
<img width="962" height="684" alt="image" src="https://github.com/user-attachments/assets/9b6dd00a-b145-4739-8b11-e6669cbf524f" />








