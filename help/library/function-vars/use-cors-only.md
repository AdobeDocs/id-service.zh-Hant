---
description: 此選用的布林值標幟可控制瀏覽器從 Experience Cloud Identity 服務要求資源的方式。
keywords: ID 服務
title: useCORSOnly
exl-id: 049a082a-8e6b-44cc-bd05-c12aaf3cbe4d
source-git-commit: 06e935a4ba4776baa900d3dc91e294c92b873c0f
workflow-type: tm+mt
source-wordcount: '145'
ht-degree: 100%

---

# useCORSOnly{#usecorsonly}

此選用的布林值標幟可控制瀏覽器從 Experience Cloud Identity 服務要求資源的方式。

**語法：** `useCORSOnly: true|false`(預設為 `false`。)

**概述**

設為 `false` 時，瀏覽器會使用 CORS 或 JSONP 執行資源檢查。但是，ID 服務總是會先嘗試透過 CORS 來要求資源。它會在不支援 CORS 的舊版瀏覽器上回復成 JSONP。如果需要強制瀏覽器只使用 CORS，請在 `useCORSOnly:true` 函數呼叫中設定 `Visitor.getInstance`。

>[!IMPORTANT]
>
>若您對於安全性有嚴格的要求，則 `Set useCORSOnly: true`。只有當您確信您的所有訪客都使用支援 CORS 的瀏覽器時，才應該啟用這個模式。不支援 CORS 的瀏覽器則不會影響用戶體驗。不過，不支援 CORS 的瀏覽器無法向 [!DNL Adobe Experience Cloud] 要求資源或交換資料。

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
