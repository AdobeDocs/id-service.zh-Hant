---
description: 此變數可讓您覆寫 AMCV Cookie 的預設期限間隔。
keywords: ID 服務
title: cookieLifetime
exl-id: bdbabdcd-a87b-412c-8c2f-3f39820f939a
source-git-commit: 06e935a4ba4776baa900d3dc91e294c92b873c0f
workflow-type: ht
source-wordcount: '50'
ht-degree: 100%

---

# cookieLifetime{#cookielifetime}

此變數可讓您覆寫 AMCV Cookie 的預設期限間隔。

根據預設，[!DNL Experience Cloud] ID 服務 Cookie 在 24 個月後過期。以秒數設定時間間隔。

**語法:** ` cookieLifetime: *`以秒為單位的期限`*`

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
