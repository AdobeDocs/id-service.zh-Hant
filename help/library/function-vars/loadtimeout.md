---
description: '設定逾時間隔 (單位: 毫秒)。用於通知其他解決方案 (例如 Analytics、Audience Manager、Target 等等)ID 服務回應的等待時間。'
keywords: ID 服務
seo-description: '設定逾時間隔 (單位: 毫秒)。用於通知其他解決方案 (例如 Analytics、Audience Manager、Target 等等)ID 服務回應的等待時間。'
seo-title: loadTimeout
title: loadTimeout
uuid: f627e044-bd73-49a4-8a90-6d19aa566751
translation-type: tm+mt
source-git-commit: bc5c81455023e22e64877bb861dfe141e158599c

---


# loadTimeout{#loadtimeout}

設定逾時間隔 (單位: 毫秒)。用於通知其他解決方案 (例如 Analytics、Audience Manager、Target 等等)ID 服務回應的等待時間。

**語法:** ` loadTimeout: *`以毫秒為單位的間隔`*`

預設值為 30,000 毫秒 (30 秒)。我們強烈建議您&#x200B;*不要*&#x200B;變更預設值。

>[!NOTE]
>
>對於頁面上的其他非 Adobe 程式碼，向 ID 服務發出的呼叫是非同步呼叫。因此，增加或減少逾時間隔不會變更頁面呈現內容的比率。不過，長時間的逾時間隔可能會影響一般網路監控工具測量的頁面載入時間，但是呈現時間不會受到影響。

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

