---
description: 設定逾時間隔 (單位：毫秒)。 用於告知其他解決方案（例如Analytics、Audience Manager、Target等） ID服務傳回回應要等候多久。
keywords: ID 服務
title: loadTimeout
exl-id: 485264f4-ee24-4042-8be3-259e70462110
TQID: https://experienceleague.adobe.com/w0-c0ROMsYRLqlHQuBfSAdardHnMfaJ8oTLf1xwL9QQ
product_v2: id: e1971122-7081-4556-9222-8a31bd71800c
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554id: c66ffd68-0f65-42bb-aa23-b4020f12e0bdid: f8a45b24-4be7-4f1b-909b-60d06b483a20id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
source-git-commit: 5c41e39a833b527a329f62e5f0929445f47139de
workflow-type: tm+mt
source-wordcount: 143
ht-degree: 69%

---

# loadTimeout{#loadtimeout}

設定逾時間隔 (單位：毫秒)。 用於告知其他解決方案（例如Analytics、Audience Manager、Target等） ID服務傳回回應要等候多久。

**語法:** `loadTimeout: *`以毫秒為單位的間隔`*`

預設值為 30,000 毫秒 (30 秒)。 我們強烈建議您&#x200B;*不要*&#x200B;變更預設值。

>[!NOTE]
>
>對於頁面上的其他非 Adobe 程式碼，向 ID 服務發出的呼叫是非同步呼叫。 因此，增加或減少逾時間隔並不會改變您的頁面轉譯內容的速度。 然而，長的逾時間隔可能會影響由常用網路監控工具所測量的頁面載入時間，但轉譯時間則不受影響。

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

