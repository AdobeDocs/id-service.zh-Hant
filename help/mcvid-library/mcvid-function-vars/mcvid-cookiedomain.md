---
description: 多部分、頂級網域需要此變數，其中 URL 最後 2 個部分的其中一個部分大於兩個字元。
keywords: ID 服務
seo-description: 多部分、頂級網域需要此變數，其中 URL 最後 2 個部分的其中一個部分大於兩個字元。
seo-title: cookieDomain
title: cookieDomain
uuid: a57e5477-c07 b-4d54-8aea-8e8 b152 f1423
translation-type: tm+mt
source-git-commit: bb687c1cd14aae7faef2565dcf9d041a1c06e3bd

---


# cookieDomain{#cookiedomain}

多部分、頂級網域需要此變數，其中 URL 最後 2 個部分的其中一個部分大於兩個字元。

**語法：**` cookieDomain: " *`URL`*"` (不需要 `www` 前置詞)。

**使用個案**

* 必填: `www.example.com.uk`
* 不需要： `www.example.co.uk`

**程式碼範例**

```js
var visitor = Visitor.getInstance ("Insert Experience Cloud organization ID here",{ 
   trackingServer: "Insert tracking server here here",  //Same as s.trackingServer 
   trackingServerSecure: "Insert secure tracking server here",  //Same as s.trackingServerSecure 
 
   //For CNAME support only. Exclude these variables if you're not using CNAME 
   marketingCloudServer: "Insert tracking server here", 
   marketingCloudServerSecure: "Insert secure tracking server here", 
 
   //Function variable 
   cookieDomain:"example.com.uk" 
});
```

