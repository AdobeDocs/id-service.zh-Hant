---
description: 多部分、頂級網域需要此變數，其中 URL 最後 2 個部分的其中一個部分大於兩個字元。
keywords: ID 服務
title: cookieDomain
exl-id: 280416ad-372a-4a59-a938-0f49c0ce300f
source-git-commit: 06e935a4ba4776baa900d3dc91e294c92b873c0f
workflow-type: ht
source-wordcount: '56'
ht-degree: 100%

---

# cookieDomain{#cookiedomain}

多部分、頂級網域需要此變數，其中 URL 最後 2 個部分的其中一個部分大於兩個字元。

**語法:** ` cookieDomain: " *`URL`*"` (前置詞 `www` 非必要)。

**使用案例**

* 必填：`www.example.com.uk`
* 非必要：`www.example.co.uk`

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
