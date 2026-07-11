---
description: 此選用的布林值標幟可控制瀏覽器從訪客ID服務要求資源的方式。
keywords: 訪客 ID 服務
title: useCORSOnly
exl-id: 049a082a-8e6b-44cc-bd05-c12aaf3cbe4d
TQID: https://experienceleague.adobe.com/QMYUbL2y8X5gSUcLmYnKZnp5mfEu7-uiogOx3rx2dkY
product_v2: id: e1971122-7081-4556-9222-8a31bd71800c
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554id: c66ffd68-0f65-42bb-aa23-b4020f12e0bdid: f8a45b24-4be7-4f1b-909b-60d06b483a20id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2: id: d095671a-1355-40aa-8b5f-06c33c68080b
source-git-commit: 09ee359440c122702a6ce83708c98af3862c9cc9
workflow-type: tm+mt
source-wordcount: 147
ht-degree: 46%

---

# useCORSOnly{#usecorsonly}

此選用的布林值標幟可控制瀏覽器從訪客ID服務要求資源的方式。

**語法：** `useCORSOnly: true|false`(預設為 `false`。)

**概觀**

設為 `false` 時，瀏覽器會使用 CORS 或 JSONP 執行資源檢查。 不過，訪客ID服務總是會先嘗試透過CORS來要求資源。 它會在不支援 CORS 的舊版瀏覽器上回復成 JSONP。 如果需要強制瀏覽器只使用 CORS，請在 `useCORSOnly:true` 函數呼叫中設定 `Visitor.getInstance`。

>[!IMPORTANT]
>
>若您對於安全性有嚴格的要求，則 `Set useCORSOnly: true`。 只有當您確信您的所有訪客都使用支援CORS的瀏覽器時，才應該啟用此模式。 不支援 CORS 的瀏覽器則不會影響用戶體驗。 不過，不支援CORS的瀏覽器無法向Adobe CX Enterprise要求資源或交換資料。

**程式碼範例**

```js
var visitor = Visitor.getInstance ("INSERT-IMS-ORG-ID-HERE",{ 
   trackingServer: "Insert tracking server here here",  //Same as s.trackingServer 
   trackingServerSecure: "Insert secure tracking server here",  //Same as s.trackingServerSecure 
 
   //For CNAME support only. Exclude these variables if you're not using CNAME 
   marketingCloudServer: "Insert tracking server here", 
   marketingCloudServerSecure: "Insert secure tracking server here", 
 
   //Function variable 
   useCORSOnly: true 
});
```

