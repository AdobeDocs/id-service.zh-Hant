---
description: 此變數可讓您覆寫 AMCV Cookie 的預設期限間隔。
keywords: ID 服務
seo-description: 此變數可讓您覆寫 AMCV Cookie 的預設期限間隔。
seo-title: cookieLifetime
title: cookieLifetime
uuid: cd945db3-429a-4625-ac3 f-69ac259377 a3
translation-type: tm+mt
source-git-commit: bb687c1cd14aae7faef2565dcf9d041a1c06e3bd

---


# cookieLifetime{#cookielifetime}

此變數可讓您覆寫 AMCV Cookie 的預設期限間隔。

根據預設 [!DNL Experience Cloud] ，ID服務Cookie會在24個月後過期。以秒數設定時間間隔。

**語法：**` cookieLifetime: *`期限(秒)`*`

**程式碼範例**

```js
var visitor = Visitor.getInstance ("Insert Experience Cloud organization ID here",{ 
   trackingServer: "Insert tracking server here here",  //Same as s.trackingServer 
   trackingServerSecure: "Insert secure tracking server here",  //Same as s.trackingServerSecure 
 
   //For CNAME support only. Exclude these variables if you're not using CNAME 
   marketingCloudServer: "Insert tracking server here", 
   marketingCloudServerSecure: "Insert secure tracking server here", 
 
   //Function variable. Example changes expiration period to 12-months. 
   cookieLifetime:31536000 
});
```

