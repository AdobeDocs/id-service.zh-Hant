---
description: 此設定可讓您根據升級的 ID 服務版本，清除孤立的或過期的 Experience Cloud ID (ECID)。
keywords: ID 服務
title: resetBeforeVersion
exl-id: 9fa40baa-433d-4f16-824b-521948a92a4b
source-git-commit: 06e935a4ba4776baa900d3dc91e294c92b873c0f
workflow-type: tm+mt
source-wordcount: '249'
ht-degree: 100%

---

# resetBeforeVersion{#resetbeforeversion}

此設定可讓您根據升級的 ID 服務版本，清除孤立的或過期的 Experience Cloud ID (ECID)。

將 `resetBeforeVersion` 變數的值設為您的 ID 服務版本，會導致過期的 ECID 從用戶端 ID 中清除。

某些情況 (例如工作階段逾時) 可能會在 ID 服務無法順利取得伺服器端 ID 的情況下產生用戶端 ID。發生這種情況時，ID 服務會追蹤孤立的用戶端 ID，而無法跨網域進行追蹤或是與其他解決方案正確同步。此行為會比對目前 AMCV Cookie 與 `resetBeforeVersion` 的值。如果任一方的 Cookie 不存在，或 Cookie 的版本小 (低) 於 `resetBeforeVersion` 的最新發行版本，則 AMCV Cookie 會遭到移除，且 ID 服務會要求全新 ECID。

若用戶的瀏覽器上存有第三方的 Demdex Cookie，則系統會檢查 ECID，以確定 ECID 是否正確使用 Demdex Cookie 中的 UUID 來產生。如果這項檢查證明該情況屬實，則新的 ECID 將會相同，而且訪客將會被視為新訪客。如果因為某個理由而未使用 Demdex Cookie 產生正被清理的 ECID，或是沒有任何 Demdex Cookie，該訪客將收到新的 ECID 而且會被視為新訪客。

**語法:** `resetBeforeVersion = "3.3"`

**程式碼範例**

```js
//Call the ID service 
var visitor = Visitor.getInstance ("Insert Marketing Cloud organization ID here", { 
  
    //Same as s.trackingServer 
    trackingServer: "Insert tracking server here ", 
  
    //Same as s.trackingServerSecure 
    trackingServerSecure: "Insert secure tracking server here", 
  
    //For CNAME support only. Exclude these variables if you're not using CNAME 
    marketingCloudServer: "Insert tracking server here", 
    marketingCloudServerSecure: "Insert secure tracking server here", 
  
    //Changing the version 
    resetBeforeVersion: "3.3" 
});
```
