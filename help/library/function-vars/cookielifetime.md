---
description: 此變數可讓您覆寫 AMCV Cookie 的預設期限間隔。
keywords: ID 服務
title: cookieLifetime
exl-id: bdbabdcd-a87b-412c-8c2f-3f39820f939a
TQID: https://experienceleague.adobe.com/EBAkG9W3VE4p7Xd5NkegOtFDNo6qBOKrKRaBUYwwJog
product_v2:
  - id: e1971122-7081-4556-9222-8a31bd71800c
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: f8a45b24-4be7-4f1b-909b-60d06b483a20
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
source-git-commit: 5c41e39a833b527a329f62e5f0929445f47139de
workflow-type: tm+mt
source-wordcount: 51
ht-degree: 100%

---

# cookieLifetime{#cookielifetime}

此變數可讓您覆寫 AMCV Cookie 的預設期限間隔。

根據預設，[!DNL Experience Cloud] ID 服務 Cookie 在 24 個月後過期。 以秒數設定時間間隔。

**語法:** `cookieLifetime: *`以秒為單位的期限`*`

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

