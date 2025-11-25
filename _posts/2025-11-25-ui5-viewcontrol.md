---
title: "[UI5] Working with Views & Controllers"
excerpt: "화면을 그리는 Views & 이벤트를 구현하는 Controllers"

categories:
  - UI5
tags:
  - [UI5]

permalink: /ui5/viewcontrol/

toc: true
toc_sticky: true

date: 2025-11-25
last_modified_at: 2025-11-25
---

<img width="1536" height="1024" alt="image" src="https://github.com/user-attachments/assets/60f36cd6-ed31-43e3-954b-f31b8c1b260d" />

---

# Model View Controller (MVC)
<img width="1288" height="660" alt="image" src="https://github.com/user-attachments/assets/e04d0a56-b996-4218-8609-01765bfde944" />

* 화면(UI)과 로직(Controller)과 데이터(Model)를 분리해서 개발하는 아키텍처 패턴.
  
|구성|역할|SAPUI5 예|
|------|---|---|
|Model|데이터 관리|JSONModel, ODataModel|
|View|화면 정의|XML View|
|Controller|이벤트·로직 처리|.controller.js|

> "Model은 데이터, View는 화면, Controller는 행동"

---
## Views
지금까지는 text, button 만들어서 body에 달았는데,  
이제는 view를 만들어서 body에 다는 작업을 수행할 것이다. 

&nbsp;  

## View Types 3가지
1. `XML view` 권장한다. xml tag를 이용한다.  
   *<mvc.View ~… → xml ver.*  
2. `JSON view` 거의 사용하지 않는다.  
3. `Typed view` (using JS) 코딩으로 만들기에 dynamic한 UI 생성이 가능하다.  
    *var oText = new sap.m.Text… → js ver.*  

&nbsp;  

### XML views
SAPUI5 > Module(index.js) > View > body  
SAP UI5가 구동되면, 모듈을 구동하고, 모듈이 뷰를 생성하고, 이게 화면에 달라붙는다. 

&nbsp;

**index.js**  
```javascript
sap.ui.define(["sap/ui/core/mvc/XMLView"], function(XMLView) {
    //App 뷰를 생성하고, 해당 view를 body에 출력한다. 
    XMLView.create({
        id: "App",
        viewName: "com.sap.training33.sapui533/view/App"  // <- 경로 잡아주기
    }).then(function (oView) {   // <-then 로딩이 다 되고 나면, 파라미터 oView가 넘어가 
        oView.placeAt("content");
    });
});
```

**App.view.xml**  
```xml
<mvc:View controllerName="com.sap.training33.sapui533.controller.App"
    displayBlock="true"
    xmlns:mvc="sap.ui.core.mvc"
    xmlns="sap.m">

    <Text id="text1" text="XML View"></Text>
</mvc:View>
```

&nbsp;  

**결과**
<img width="639" height="163" alt="image" src="https://github.com/user-attachments/assets/286bd724-d2ef-4695-9a82-6baf8e527e79" />
> 그냥 붙이는 게 아니라 view를 생성해서 붙여야 한다.
> reuse.js( =index.js)에서 주석 처리하고 뷰를 생성한다.  

&nbsp;  

---

## View Controllers
화면에서 발생한 이벤트를 수행하는 게 Controller. View와 1대1 /N대1 관계.  
이름이 같아서 짝이 아니라, view 코드에서 controllerName에 등록해줘야 짝이 되는 것!

&nbsp;  

**App.view.xml**
```xml
<mvc:View controllerName="com.sap.training33.sapui533.controller.App"
    displayBlock="true"
    xmlns:mvc="sap.ui.core.mvc"
    xmlns="sap.m">

    <Text id="text1" text="XML View"></Text>

    <Button id="button1" text="Say Hello" press=".onSayHello"/>

</mvc:View>
```
**App.controller.js**
```javascript
sap.ui.define([
  "sap/ui/core/mvc/Controller",
  "sap/m/MessageBox",
  "sap/m/MessageToast"
], (Controller, MessageBox, MessageToast) => {
  "use strict";

  return Controller.extend("com.sap.training33.sapui533.controller.App", {
      onInit() {
      },
      onSayHello: function() {
       // MessageBox.alert("Say Hello Button is clicked!");
       MessageToast.show("Say Hello Button is clicked!");
		}
  });
});
```

&nbsp;

**결과**
![20251111_1451220360](https://github.com/user-attachments/assets/3ea318d7-d4fd-4a22-86f4-4ebade58aa5b)


