---
description: 此設定可讓您根據要更新的訪客ID服務版本，清除孤立或過期的ECID (ECID)。
keywords: 訪客 ID 服務
title: resetBeforeVersion
exl-id: 9fa40baa-433d-4f16-824b-521948a92a4b
TQID: https://experienceleague.adobe.com/5aqi7F5QkybjotjVMJgDWCchFw1XOYa6qPOSUzDyeqE
product_v2: id: e1971122-7081-4556-9222-8a31bd71800c
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554id: c66ffd68-0f65-42bb-aa23-b4020f12e0bdid: f8a45b24-4be7-4f1b-909b-60d06b483a20id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
source-git-commit: 09ee359440c122702a6ce83708c98af3862c9cc9
workflow-type: tm+mt
source-wordcount: 257
ht-degree: 41%

---

# resetBeforeVersion{#resetbeforeversion}

此設定可讓您根據要更新的訪客ID服務版本，清除孤立或過期的ECID (ECID)。

將您的訪客ID服務版本當作`resetBeforeVersion`變數的值提供，會導致過期的ECID從使用者端ID中清除。

某些情況（例如工作階段逾時）可能會造成使用者端ID的產生，而訪客ID服務無法成功取得伺服器端ID。 發生這種情況時，訪客ID服務會追蹤孤立的使用者端ID，而無法跨網域進行追蹤或與其他解決方案正確同步。 此行為會比對目前 AMCV Cookie 與 `resetBeforeVersion` 的值。 如果任一方的Cookie不存在，或Cookie的版本小（低）於`resetBeforeVersion`的最新發行版本，則AMCV Cookie會遭到移除，且訪客ID服務會要求全新ECID。

若用戶的瀏覽器上存有第三方的 Demdex Cookie，則系統會檢查 ECID，以確定 ECID 是否正確使用 Demdex Cookie 中的 UUID 來產生。 如果這項檢查證明該情況屬實，則新的 ECID 將會相同，而且訪客將會被視為新訪客。 如果因為某個理由而未使用 Demdex Cookie 產生正被清理的 ECID，或是沒有任何 Demdex Cookie，該訪客將收到新的 ECID 而且會被視為新訪客。

**語法:** `resetBeforeVersion = "3.3"`

**程式碼範例**

```js
//Call the Visitor ID Service 
var visitor = Visitor.getInstance ("INSERT-IMS-ORG-ID-HERE", { 
  
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

