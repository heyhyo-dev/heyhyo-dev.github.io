---
title: "[UI5] Loading & Initializing SAPUI5"
excerpt: "Bootstrap으로 시작하기"

categories:
  - UI5
tags:
  - [UI5]

permalink: /ui5/bootstrap/

toc: true
toc_sticky: true

date: 2025-11-21
last_modified_at: 2025-11-21
---

## Bootstrapping SAPUI5
<img width="700" height="450" alt="image" src="https://github.com/user-attachments/assets/c1bfc4f2-637f-4272-a047-0163e3c2d7fd" />



> **시작하기에 앞서 ...**   
> UI5는 BAS(Business Application Studio)로, VSCode를 사용한다.   
> Entry Point가 될 수 있는 건  index.html 혹은 component.js다.  
> 오늘은 index.html의 bootstrap을 알아보자.

---
### Bootstrap
* UI5 프레임워크를 페이지에 로딩하고 초기 설정을 정의하는 역할
* 즉, UI5 앱이 실행되기 전에 필요한 설정과 라이브러리를 웹페이지에 불러오는 시동 절차

```html
    <script id="sap-ui-bootstrap"
            src="resources/sap-ui-core.js"
            data-sap-ui-theme="sap_fiori_3"
            data-sap-ui-libs="sap.m"
            data-sap-ui-compatVersion="edge"
    ></script>
```
* src="resources/sap-ui-core.js"  
  : UI5 코어(Core) 라이브러리를 어디서 가져올지 지정   
* data-sap-ui-theme="sap_fiori_3"  
  : UI5 애플리케이션에서 사용할 테마(Theme) 설정    
* data-sap-ui-libs="sap.m"  
  : 필요한 UI5 라이브러리(Controls)를 로딩  
* data-sap-ui-compatVersion="edge"  
  : UI5의 호환성 버전 설정 -> edge는 최신 기능을 우선으로 사용하는 모드  



### index.html 전체 코드 
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <title>SAPUI5 Fiori App</title>
    <style>
        html, body, body > div, #container, #container-uiarea {
            height: 100%;
        }
    </style>
    <script id="sap-ui-bootstrap"
            src="resources/sap-ui-core.js"
            data-sap-ui-theme="sap_fiori_3"
            data-sap-ui-libs="sap.m"
            data-sap-ui-compatVersion="edge"
    ></script>

    <script>
        //나만의 고유 로직 구현
    </script>
</head>
<body id="content">
</body>
</html>
```




