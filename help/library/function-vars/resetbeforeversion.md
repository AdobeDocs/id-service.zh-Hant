---
description: 此設定可讓您根據升級的 ID 服務版本，清除孤立的或過期的 Experience Cloud ID (ECID)。
keywords: ID Service
seo-description: 此設定可讓您根據升級的 ID 服務版本，清除孤立的或過期的 Experience Cloud ID (ECID)。
seo-title: resetBeforeVersion
title: resetBeforeVersion
uuid: b00d18b8-6720-42f9-9c83-bd306184cc0c
translation-type: tm+mt
source-git-commit: bc5c81455023e22e64877bb861dfe141e158599c
workflow-type: tm+mt
source-wordcount: '268'
ht-degree: 60%

---


# resetBeforeVersion{#resetbeforeversion}

此設定可讓您根據升級的 ID 服務版本，清除孤立的或過期的 Experience Cloud ID (ECID)。

將 `resetBeforeVersion` 變數的值設為您的 ID 服務版本，會導致過期的 ECID 從用戶端 ID 中清除。

某些條件（例如作業逾時）有時會導致在ID服務未成功取得伺服器端ID的情況下產生用戶端ID。 發生此情況時，ID服務會追蹤孤立的用戶端ID，而無法跨網域追蹤或與其他解決方案正確同步。 此行為會比對目前 AMCV Cookie 與 `resetBeforeVersion` 的值。如果任一方的 Cookie 不存在，或 Cookie 的版本小 (低) 於 `resetBeforeVersion` 的最新發行版本，則 AMCV Cookie 會遭到移除，且 ID 服務會要求全新 ECID。

若使用者的瀏覽器上存有第三方的 Demdex Cookie，則系統會檢查 ECID，以確定 ECID 是否正確使用 Demdex Cookie 中的 UUID 來產生。如果此檢查證明為真，則新的ECID將相同，而訪客將被視為新訪客。 如果因故未使用Demdex Cookie產生清除的ECID，或沒有Demdex Cookie時，訪客會收到新的ECID，並會被視為新的ECID。

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

