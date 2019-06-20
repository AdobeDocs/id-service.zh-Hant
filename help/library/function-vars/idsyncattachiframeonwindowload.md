---
description: 選用的布林值標幟，可控制Experience Cloud ID Service如何載入ID同步iFrame。
keywords: ID 服務
seo-description: 選用的布林值標幟，可控制Experience Cloud ID Service如何載入ID同步iFrame。
seo-title: idSyncAttachIframeOnWindowLoad
title: idSyncAttachIframeOnWindowLoad
uuid: aa2c2fa4-2cab-4e08-8d35-729a6c3e459a
translation-type: tm+mt
source-git-commit: 3e7b49564938527e1b6bca3a5fbaf9eb141d2e06

---


# idSyncAttachIframeOnWindowLoad{#idsyncattachiframeonwindowload}

選用的布林值標幟，可控制Experience Cloud ID Service如何載入ID同步iFrame。

**語法：**` `idSyncAttachFrameonWindowLoad= true| false「(預設值is `false`.)

當 `idSyncAttachIframeOnWindowLoad: true` 時，ID 服務會在視窗載入時載入 ID 同步 iFrame。根據預設，ID 服務會儘快載入 ID 同步 iFrame，而非在視窗載入時才載入。

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

