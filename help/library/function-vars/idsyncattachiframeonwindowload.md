---
description: 此選用的布林值標幟可控制 Experience Cloud Identity 服務載入 ID 同步 iFrame 的方式。
keywords: ID 服務
title: idSyncAttachIframeOnWindowLoad
exl-id: 44c45378-f007-4d87-913a-d6bb9961948c
source-git-commit: 06e935a4ba4776baa900d3dc91e294c92b873c0f
workflow-type: ht
source-wordcount: '77'
ht-degree: 100%

---

# idSyncAttachIframeOnWindowLoad{#idsyncattachiframeonwindowload}

此選用的布林值標幟可控制 Experience Cloud Identity 服務載入 ID 同步 iFrame 的方式。

**語法:** ` `idSyncAttachIframeOnWindowLoad= true|false`` (預設為 `false`)。

當 `idSyncAttachIframeOnWindowLoad: true` 時，ID 服務會在視窗載入時載入 ID 同步 iFrame。根據預設，ID 服務會盡快載入 ID 同步 iFrame，而不是在視窗載入時才載入。

**程式碼範例**

```js
var visitor = Visitor.getInstance ("Insert Experience Cloud organization ID here",{ 
   trackingServer: "Insert tracking server here here",  //Same as s.trackingServer 
   trackingServerSecure: "Insert secure tracking server here",  //Same as s.trackingServerSecure 
 
   //For CNAME support only. Exclude these variables if you're not using CNAME 
   marketingCloudServer: "Insert tracking server here", 
   marketingCloudServerSecure: "Insert secure tracking server here", 
 
   //Function variable. Example loads ID sync iFrame on window load instad of ASAP. 
   idSyncAttachIframeOnWindowLoad: true 
});
```
