---
description: getInstance 可針對特定 Experience Cloud 組織 ID 傳回訪客 ID 物件。必須有此例項，才能初始化透過 s.visitor 提供給 AppMeasurement 的訪客 ID 物件。
keywords: ID 服務
seo-description: getInstance 可針對特定 Experience Cloud 組織 ID 傳回訪客 ID 物件。必須有此例項，才能初始化透過 s.visitor 提供給 AppMeasurement 的訪客 ID 物件。
seo-title: getInstance
title: getInstance
uuid: 259b88a6-e3 d0-4aab-b935-566099bdab98
translation-type: tm+mt
source-git-commit: bb687c1cd14aae7faef2565dcf9d041a1c06e3bd

---


# getInstance{#getinstance}

getInstance 可針對特定 Experience Cloud 組織 ID 傳回訪客 ID 物件。必須有此例項，才能初始化透過 s.visitor 提供給 AppMeasurement 的訪客 ID 物件。

**語法**

**JavaScript**

```js
var visitor = Visitor.getInstance("INSERT-MARKETING-CLOUD-ORGANIZATION-ID-HERE", { 
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
>*請* 勿實例化訪客函數 `var visitor = new Visitor`。您必須使用此處指出的適當函數呼叫。套用至 [!DNL VisitorAPI.js] 程式碼資料庫第三版或是更新版本。

**ActionScript/Flash**

```js
import com.adobe.mc.Visitor; 
... 
var visitor = Visitor.getInstance("INSERT-MARKETING-CLOUD-ORGANIZATION-ID-HERE", { 
     trackingServer: "INSERT-TRACKING-SERVER-HERE", // same as s.trackingServer 
     trackingServerSecure: "INSERT-SECURE-TRACKING-SERVER-HERE", // same as s.trackingServerSecure 
 
     // To enable CNAME support, add the following configuration variables 
     // If you are not using CNAME, DO NOT include these variables 
     marketingCloudServer: "INSERT-TRACKING-SERVER-HERE", 
     marketingCloudServerSecure: "INSERT-SECURE-TRACKING-SERVER-HERE" // same as s.trackingServerSecure 
});
```

如果 `getInstance` 找不到現有例項，則會建立與傳回新例項。[`s_gi()`](https://marketing.adobe.com/resources/help/en_US/sc/implement/?f=function_s_gi.html)[!DNL AppMeasurement]這與函數類似。

**常見用法**

[!DNL Experience Cloud] ID服務API會維護為每 [!DNL Adobe Experience Cloud] 個組織ID建立的所有例項清單。如果使用 ID 服務 API 的應用程式未將參照傳遞至例項，可藉由呼叫 `getInstance` 來尋找該例項，而不須建立新例項。這樣就能支援相同網頁或應用程式中，不同組織的多個例項。

對於沒有明確的 `init` 階段、卻需要在多處呼叫 ID 服務 API 的應用程式來說，這個用法很有幫助。您可以在所有位置呼叫 `getInstance`，第一個執行的 getInstance 將建立例項。後續呼叫將傳回現有的例項。
