---
description: 選用的布林值標幟，可控制瀏覽器如何從 Experience Cloud ID 服務要求資源。
keywords: ID 服務
seo-description: 選用的布林值標幟，可控制瀏覽器如何從 Experience Cloud ID 服務要求資源。
seo-title: useCORSOnly
title: useCORSOnly
uuid: 607dc035-dffc-4f4d-be51-08ef6c0a8fad
translation-type: ht
source-git-commit: bb687c1cd14aae7faef2565dcf9d041a1c06e3bd

---


# useCORSOnly{#usecorsonly}

選用的布林值標幟，可控制瀏覽器如何從 Experience Cloud ID 服務要求資源。

**語法: ** `useCORSOnly: true|false` (預設為 `false`)。

**概述**

設為 `false` 時，瀏覽器會使用 CORS 或 JSONP 執行資源檢查。不過，ID 服務一律會先嘗試用 CORS 要求資源。在不支援 CORS 的舊版瀏覽器上會回復為 JSONP 要求。如果需要強制瀏覽器只使用 CORS，請在 `useCORSOnly:true` 函數呼叫中設定 `Visitor.getInstance`。

>[!IMPORTANT]
>
>若您對於安全性有嚴格的要求，則 `Set useCORSOnly: true`。請僅在確信所有訪客使用的瀏覽器都支援 CORS 的情形下，才啟用此模式。在不支援 CORS 的瀏覽器上，使用者體驗不受影響。不過，不支援 CORS 的瀏覽器無法向 [!DNL Adobe Experience Cloud] 要求資源或交換資料。

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

