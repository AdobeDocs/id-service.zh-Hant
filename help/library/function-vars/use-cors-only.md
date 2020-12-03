---
description: 此選用的布林值標幟可控制瀏覽器從 Experience Cloud Identity 服務要求資源的方式。
keywords: ID Service
seo-description: 此選用的布林值標幟可控制瀏覽器從 Experience Cloud Identity 服務要求資源的方式。
seo-title: useCORSOnly
title: useCORSOnly
uuid: 607dc035-dffc-4f4d-be51-08ef6c0a8fad
translation-type: tm+mt
source-git-commit: e6d65f1bfed187d7440512e8f3c2de0550506c95
workflow-type: tm+mt
source-wordcount: '161'
ht-degree: 66%

---


# useCORSOnly{#usecorsonly}

此選用的布林值標幟可控制瀏覽器從 Experience Cloud Identity 服務要求資源的方式。

**語法:** `useCORSOnly: true|false` (預設為 `false`。)

**概述**

設為 `false` 時，瀏覽器會使用 CORS 或 JSONP 執行資源檢查。不過，ID服務一律會先嘗試向CORS請求資源。 在不支援CORS的舊版瀏覽器上，它會回復為JSONP。 如果需要強制瀏覽器只使用 CORS，請在 `useCORSOnly:true` 函數呼叫中設定 `Visitor.getInstance`。

>[!IMPORTANT]
>
>若您對於安全性有嚴格的要求，則 `Set useCORSOnly: true`。如果您確信所有訪客都使用支援CORS的瀏覽器，您才應啟用此模式。 不支援CORS的瀏覽器不會影響使用者體驗。 不過，不支援 CORS 的瀏覽器無法向 [!DNL Adobe Experience Cloud] 要求資源或交換資料。

**程式碼範例**

```js
var visitor = Visitor.getInstance ("Insert Experience Cloud organization ID here",{ 
   trackingServer: "Insert tracking server here here",  //Same as s.trackingServer 
   trackingServerSecure: "Insert secure tracking server here",  //Same as s.trackingServerSecure 
 
   //For CNAME support only. Exclude these variables if you're not using CNAME 
   marketingCloudServer: "Insert tracking server here", 
   marketingCloudServerSecure: "Insert secure tracking server here", 
 
   //Function variable 
   useCORSOnly: true 
});
```

