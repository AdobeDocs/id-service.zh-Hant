---
description: getInstance 會傳回指定 Experience Cloud 組織 ID 的訪客 ID 物件。在初始化透過 s.visitor 提供給 AppMeasurement 的訪客 ID 物件時，必須要有此項目。
keywords: ID Service
seo-description: getInstance 會傳回指定 Experience Cloud 組織 ID 的訪客 ID 物件。在初始化透過 s.visitor 提供給 AppMeasurement 的訪客 ID 物件時，必須要有此項目。
seo-title: getInstance
title: getInstance
uuid: 259b88a6-e3d0-4aab-b935-566099bdab98
translation-type: ht
source-git-commit: d2bc0e7fedc4e48d51f5dad158f9f8bfcb0cb4f3
workflow-type: ht
source-wordcount: '254'
ht-degree: 100%

---


# getInstance{#getinstance}

getInstance 會傳回指定 Experience Cloud 組織 ID 的訪客 ID 物件。在初始化透過 s.visitor 提供給 AppMeasurement 的訪客 ID 物件時，必須要有此項目。

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
>*請勿*&#x200B;以 `var visitor = new Visitor` 實例化 Visitor 函數。您必須使用此處指出的適當函數呼叫。套用至 [!UICONTROL VisitorAPI.js] 程式碼程式庫 3.0 版或更新版本。

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

如果 `getInstance` 找不到現有例項，則會建立與傳回新例項。這類似於 [!DNL AppMeasurement] 中的 [ `s_gi()` 函數 ](https://docs.adobe.com/content/help/zh-Hant/analytics/implementation/vars/functions/s-gi.html)。

**常見用法**

[!DNL Experience Cloud] ID 服務 API 維護為每個 [!DNL Adobe Experience Cloud] 組織 ID 建立的所有例項清單。如果使用 ID 服務 API 的應用程式未將參照傳遞至例項，可藉由呼叫 `getInstance` 來尋找該例項，而不須建立新例項。這樣就能支援相同網頁或應用程式中，不同組織的多個例項。

對於沒有明確的 `init` 階段、卻需要在多處呼叫 ID 服務 API 的應用程式來說，這個用法很有幫助。您可以在所有位置呼叫 `getInstance`，第一個執行的 getInstance 將建立例項。後續呼叫將傳回現有的例項。
