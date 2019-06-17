---
description: 此設定可讓您根據升級的 ID 服務版本，清除孤立的或過期的 Experience Cloud ID (ECID)。
keywords: ID 服務
seo-description: 此設定可讓您根據升級的 ID 服務版本，清除孤立的或過期的 Experience Cloud ID (ECID)。
seo-title: resetBeforeVersion
title: resetBeforeVersion
uuid: b00d18b8-6720-42f9-9c83-bd306184 cc0 c
translation-type: tm+mt
source-git-commit: bb687c1cd14aae7faef2565dcf9d041a1c06e3bd

---


# resetBeforeVersion{#resetbeforeversion}

此設定可讓您根據升級的 ID 服務版本，清除孤立的或過期的 Experience Cloud ID (ECID)。

將 `resetBeforeVersion` 變數的值設為您的 ID 服務版本，會導致過期的 ECID 從用戶端 ID 中清除。

在某些情況下，例如工作階段逾時，有時候可能會造成用戶端 ID 在 ID 服務未成功取得伺服器端 ID 時便產生。當發生這種情況時，ID 服務會追蹤孤立的用戶端 ID，卻無法跨越網域追蹤孤立 ID，或與其他解決方案正確同步。此行為會比對目前 AMCV Cookie 與 `resetBeforeVersion` 的值。如果任一方的 Cookie 不存在，或 Cookie 的版本小 (低) 於 `resetBeforeVersion` 的最新發行版本，則 AMCV Cookie 會遭到移除，且 ID 服務會要求全新 ECID。

若使用者的瀏覽器上存有第三方的 Demdex Cookie，則系統會檢查 ECID，以確定 ECID 是否正確使用 Demdex Cookie 中的 UUID 來產生。如果這項檢查證實為真，則新 ECID 會保持不變，且訪客會視為新訪客。如出於某些原因，使得遭清除的 ECID 並非使用 Demdex Cookie 產生，或如果 Demdex Cookie 不存在，則訪客會收到新的 ECID，且會視為新訪客。

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

