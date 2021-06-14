---
description: 設定逾時間隔 (單位：毫秒)。用來告知其他解決方案 (例如 Analytics、Audience Manager、Target 等)ID 服務傳回回應要等候多久。
keywords: ID 服務
title: loadTimeout
exl-id: 485264f4-ee24-4042-8be3-259e70462110
source-git-commit: 06e935a4ba4776baa900d3dc91e294c92b873c0f
workflow-type: ht
source-wordcount: '140'
ht-degree: 100%

---

# loadTimeout{#loadtimeout}

設定逾時間隔 (單位：毫秒)。用來告知其他解決方案 (例如 Analytics、Audience Manager、Target 等)ID 服務傳回回應要等候多久。

**語法:** ` loadTimeout: *`以毫秒為單位的間隔`*`

預設值為 30,000 毫秒 (30 秒)。我們強烈建議您&#x200B;*不要*&#x200B;變更預設值。

>[!NOTE]
>
>對於頁面上的其他非 Adobe 程式碼，向 ID 服務發出的呼叫是非同步呼叫。因此，增加或減少逾時間隔並不會改變您的頁面轉譯內容的速度。然而，長的逾時間隔可能會影響由常用網路監控工具所測量的頁面載入時間，但轉譯時間則不受影響。

**程式碼範例**

```js
var visitor = Visitor.getInstance ("Insert Experience Cloud organization ID here",{ 
   trackingServer: "Insert tracking server here here",  //Same as s.trackingServer 
   trackingServerSecure: "Insert secure tracking server here",  //Same as s.trackingServerSecure 
 
   //For CNAME support only. Exclude these variables if you're not using CNAME 
   marketingCloudServer: "Insert tracking server here", 
   marketingCloudServerSecure: "Insert secure tracking server here", 
 
   //Function variable. Example sets the timeout to 10,000 milliseconds (10 seconds). 
   loadTimeout:10000 
});
```
