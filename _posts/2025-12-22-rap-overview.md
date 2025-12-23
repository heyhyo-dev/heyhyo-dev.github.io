---
title: "[RAP] 개요"
excerpt: "개념/필요성/종류 "

categories:
  - RAP
tags:
  - [RAP]

permalink: /rap/overview/

toc: true
toc_sticky: true

date: 2025-12-22
last_modified_at: 2025-12-22
---

# RAP란?  
* RESTful ABAP Programming의 약자  
* SAP 클라우드 플랫폼 및 S/4HANA 환경에서 비즈니스 애플리케이션을 빠르고 효율적으로 개발하기 위한 프레임워크(뼈대,틀)

# 왜 사용하는가? 
1. Classic ABAP의 한계 : 기존 개발 방식으로는 현대 웹 환경과 클라우드 요구사항 충족하기 어려움.  
2. Fiori 최적화 : 표준화된 아키텍쳐로, SEGW에서의 OData 활성화 없이 CDS View에 어노테이션을 추가하는 것만으로도 UI 생성 가능. 

## 기존 GUI와의 차별점은?  
<img width="819" height="233" alt="image" src="https://github.com/user-attachments/assets/00f79899-a796-4da5-a69e-e909c4b7994d" />


# 3단계 구조
* 데이터 모델링(CDS)
* 비즈니스 로직(Behavior)
* 서비스 노출(Service Definition/Binding)

# 종류
> 표준 동작(CRUD)을 누가 처리하느냐가 큰 차이점!

## Managed RAP
* 프레임워크가 CRUD를 자동으로 처리한다.  
* 사용자가 화면에서 '저장'을 누르면, RAP 프레임워크가 알아서 Transactional Buffer를 생성한다.  
  -> Buffer : 데이터가 DB에 가기 전 머무는 임시 공간.
* 보통 신규 개발 프로그램 등  

## Unmanaged RAP
* 개발자가 직접 CRUD 로직을 넣는다.
* 사용자가 '저장'을 누르면, 프레임워크는 개발자가 만든 Class의 Method 호출만 한다. 실제 저장 로직은 개발자가 구현한다.  
* 보통 AS-IS 참고하여 개발하는 프로그램 / 여러 테이블 강제 업데이트하는 경우 등  

