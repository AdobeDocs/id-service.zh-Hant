---
description: 此設定可讓您根據升級的 ID 服務版本，清除孤立的或過期的 Experience Cloud ID (ECID)。
keywords: ID 服務
title: resetBeforeVersion
exl-id: 9fa40baa-433d-4f16-824b-521948a92a4b
TQID: https://experienceleague.adobe.com/5aqi7F5QkybjotjVMJgDWCchFw1XOYa6qPOSUzDyeqE
product_v2: id: e1971122-7081-4556-9222-8a31bd71800c
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554id: c66ffd68-0f65-42bb-aa23-b4020f12e0bdid: f8a45b24-4be7-4f1b-909b-60d06b483a20id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
source-git-commit: 5c41e39a833b527a329f62e5f0929445f47139de
workflow-type: tm+mt
source-wordcount: 254
ht-degree: 87%

---

# resetBeforeVersion{#resetbeforeversion}

此設定可讓您根據升級的 ID 服務版本，清除孤立的或過期的 Experience Cloud ID (ECID)。

將 `resetBeforeVersion` 變數的值設為您的 ID 服務版本，會導致過期的 ECID 從用戶端 ID 中清除。

某些情況 (例如工作階段逾時) 可能會在 ID 服務無法順利取得伺服器端 ID 的情況下產生用戶端 ID。 發生這種情況時，ID 服務會追蹤孤立的用戶端 ID，而無法跨網域進行追蹤或是與其他解決方案正確同步。 此行為會比對目前 AMCV Cookie 與 `resetBeforeVersion` 的值。 如果任一方的Cookie不存在，或Cookie的版本小（低）於`resetBeforeVersion`的最新發行版本，則AMCV Cookie會遭到移除，且ID服務會要求全新ECID。

若用戶的瀏覽器上存有第三方的 Demdex Cookie，則系統會檢查 ECID，以確定 ECID 是否正確使用 Demdex Cookie 中的 UUID 來產生。 如果這項檢查證明該情況屬實，則新的 ECID 將會相同，而且訪客將會被視為新訪客。 如果因為某個理由而未使用 Demdex Cookie 產生正被清理的 ECID，或是沒有任何 Demdex Cookie，該訪客將收到新的 ECID 而且會被視為新訪客。

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

