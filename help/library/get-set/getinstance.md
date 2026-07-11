---
description: getInstance會傳回指定IMS組織ID的訪客ID物件。 在初始化透過 s.visitor 提供給 AppMeasurement 的訪客 ID 物件時，必須要有此項目。
keywords: 訪客 ID 服務
title: getInstance
exl-id: 4941cf51-a8d0-4796-a102-4cd13cd5574d
TQID: https://experienceleague.adobe.com/XtjVkeuXAke6g-K8DNmq5kT6aUszrj6W0k9UM2NBBIA
product_v2:
  - id: e1971122-7081-4556-9222-8a31bd71800c
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: f8a45b24-4be7-4f1b-909b-60d06b483a20
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
  - id: c2be0313-b3ae-45e0-b454-d20bf54b23f2
source-git-commit: 09ee359440c122702a6ce83708c98af3862c9cc9
workflow-type: tm+mt
source-wordcount: 230
ht-degree: 55%

---

# getInstance{#getinstance}

getInstance會傳回指定IMS組織ID的訪客ID物件。 在初始化透過 s.visitor 提供給 AppMeasurement 的訪客 ID 物件時，必須要有此項目。

**語法**

**JavaScript**

```js
var visitor = Visitor.getInstance("INSERT-IMS-ORG-ID-HERE", { 
     trackingServer: "INSERT-TRACKING-SERVER-HERE", // same as s.trackingServer 
     trackingServerSecure: "INSERT-SECURE-TRACKING-SERVER-HERE", // same as s.trackingServerSecure 
 
     // To enable CNAME support, add the following configuration variables 
     // If you are not using CNAME, DO NOT include these variables 
     marketingCloudServer: "INSERT-TRACKING-SERVER-HERE", 
     marketingCloudServerSecure: "INSERT-SECURE-TRACKING-SERVER-HERE" // same as s.trackingServerSecure 
});
```

>[!CAUTION]
>
>*請勿*&#x200B;以 `var visitor = new Visitor` 實例化 Visitor 函數。 您必須使用此處指出的適當函數呼叫。 套用至 `VisitorAPI.js` 程式碼資料庫第三版或是更新版本。

**ActionScript/Flash**

```js
import com.adobe.mc.Visitor; 
... 
var visitor = Visitor.getInstance("INSERT-IMS-ORG-ID-HERE", { 
     trackingServer: "INSERT-TRACKING-SERVER-HERE", // same as s.trackingServer 
     trackingServerSecure: "INSERT-SECURE-TRACKING-SERVER-HERE", // same as s.trackingServerSecure 
 
     // To enable CNAME support, add the following configuration variables 
     // If you are not using CNAME, DO NOT include these variables 
     marketingCloudServer: "INSERT-TRACKING-SERVER-HERE", 
     marketingCloudServerSecure: "INSERT-SECURE-TRACKING-SERVER-HERE" // same as s.trackingServerSecure 
});
```

如果 `getInstance` 找不到現有例項，則會建立與傳回新例項。 這類似於AppMeasurement中的[`s_gi()`函式](https://experienceleague.adobe.com/docs/analytics/implementation/vars/functions/s-gi.html?lang=zh-Hant)。

**常見用法**

訪客ID服務API維護為每個IMS組織ID建立的所有執行個體清單。 如果使用訪客ID服務API的應用程式未傳遞執行個體的參考，可呼叫`getInstance`來尋找該執行個體，而不建立新執行個體。 這樣就能支援相同網頁或應用程式中，不同組織的多個例項。

對於沒有明確的`init`階段、但需要在多個位置呼叫訪客ID服務API的應用程式來說，這個用法很有用。 您可以在所有位置呼叫 `getInstance`，第一個執行的 getInstance 將建立例項。 後續呼叫將傳回現有的例項。

