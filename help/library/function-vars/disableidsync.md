---
description: 選用的布林值標幟，可停用 ID 同步。
keywords: ID 服務
seo-description: 選用的布林值標幟，可停用 ID 同步。
seo-title: disableIdSyncs
title: disableIdSyncs
uuid: 8bea1de8-53c8-4a15-bcf5-f0869763a32e
exl-id: 96d42133-6040-4da3-9315-fd94318b33aa
translation-type: ht
source-git-commit: 4453ebf701ea2dc06e6093dd77be6eb0f3b2936e
workflow-type: ht
source-wordcount: '46'
ht-degree: 100%

---

# disableIdSyncs{#disableidsyncs}

選用的布林值標幟，可停用 ID 同步。

>[!NOTE]
>
>此設定原為 `idSyncDisableSyncs`，已在 2018 年 1 月 18 日發行的 v3.0 版本中重新命名為 `disableIdSyncs`。

**語法:** `disableIdSyncs: true|false` (預設為 `false`。)

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
