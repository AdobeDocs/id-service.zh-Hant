---
description: 此選用的布林值標幟可控制訪客ID服務載入ID同步iFrame的方式。
keywords: 訪客 ID 服務
title: idSyncAttachIframeOnWindowLoad
exl-id: 44c45378-f007-4d87-913a-d6bb9961948c
TQID: https://experienceleague.adobe.com/fEqtHlUaNadgatKX-V-7FuZn-WTZOFg-YtBOD7yKg0k
product_v2:
  - id: e1971122-7081-4556-9222-8a31bd71800c
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: f8a45b24-4be7-4f1b-909b-60d06b483a20
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
source-git-commit: 09ee359440c122702a6ce83708c98af3862c9cc9
workflow-type: tm+mt
source-wordcount: 78
ht-degree: 16%

---

# idSyncAttachIframeOnWindowLoad{#idsyncattachiframeonwindowload}

此選用的布林值標幟可控制訪客ID服務載入ID同步iFrame的方式。

**語法:** ` `idSyncAttachIframeOnWindowLoad= true|false&grave;&grave; (預設為 `false`)。

當`idSyncAttachIframeOnWindowLoad: true`時，訪客ID服務會在視窗載入時載入ID同步iFrame。 根據預設，訪客ID服務會儘快載入ID同步iFrame，而不是在視窗載入時才載入。

**程式碼範例**

```js
var visitor = Visitor.getInstance ("INSERT-IMS-ORG-ID-HERE",{ 
   trackingServer: "Insert tracking server here here",  //Same as s.trackingServer 
   trackingServerSecure: "Insert secure tracking server here",  //Same as s.trackingServerSecure 
 
   //For CNAME support only. Exclude these variables if you're not using CNAME 
   marketingCloudServer: "Insert tracking server here", 
   marketingCloudServerSecure: "Insert secure tracking server here", 
 
   //Function variable. Example loads ID sync iFrame on window load instad of ASAP. 
   idSyncAttachIframeOnWindowLoad: true 
});
```

