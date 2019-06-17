---
description: 選用的布林值標幟，可停用 ID 同步。
keywords: ID 服務
seo-description: 選用的布林值標幟，可停用 ID 同步。
seo-title: disableIdSyncs
title: disableIdSyncs
uuid: bea1de8-53c8-4a15-bcf5-f0869763 a32 e
translation-type: tm+mt
source-git-commit: bb687c1cd14aae7faef2565dcf9d041a1c06e3bd

---


# disableIdSyncs{#disableidsyncs}

選用的布林值標幟，可停用 ID 同步。

>[!NOTE]
>
>2018年月18日發行的版本中， `idSyncDisableSyncs` 此 `disableIdSyncs` 組態已重新命名並重新命名。

**語法：**`disableIdSyncs: true|false` (預設 `false`為。)

**程式碼範例**

```js
var visitor = Visitor.getInstance ("Insert Experience Cloud organization ID here",{ 
   trackingServer: "Insert tracking server here here",  //Same as s.trackingServer 
   trackingServerSecure: "Insert secure tracking server here",  //Same as s.trackingServerSecure 
 
   //For CNAME support only. Exclude these variables if you're not using CNAME 
   marketingCloudServer: "Insert tracking server here", 
   marketingCloudServerSecure: "Insert secure tracking server here", 
 
   //Function variable 
   disableIdSyncs: true 
});
```

