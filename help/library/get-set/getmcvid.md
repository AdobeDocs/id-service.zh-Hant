---
description: getMarketingCloudVisitorID會傳回ECID。
keywords: 訪客 ID 服務
title: getMarketingCloudVisitorID
exl-id: bd81cc0b-0511-492d-beb8-8ba2fe5d4323
TQID: https://experienceleague.adobe.com/Ltpdq4dlGbJ8h0vAZBD52Pq7gLaurxSDYqETkLqQfDw
product_v2:
  - id: e1971122-7081-4556-9222-8a31bd71800c
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: f8a45b24-4be7-4f1b-909b-60d06b483a20
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
source-git-commit: 09ee359440c122702a6ce83708c98af3862c9cc9
workflow-type: tm+mt
source-wordcount: 118
ht-degree: 52%

---

# getMarketingCloudVisitorID{#getmarketingcloudvisitorid}

getMarketingCloudVisitorID會傳回ECID。

**語法:** `var *`變數名稱`* = visitor.getMarketingCloudVisitorID()`

此方法通常會用於需要讀取訪客 ID 的自訂解決方案。 標準實作不會使用此函數。 `getMarketingCloudVisitorID`也會使用回呼函式讀取Analytics ID，並將它們帶入您的系統或應用程式。

```js
//callback function 
var useMarketingCloudID = function(id){ 
     //whatever your function does with the ECID 
}; 
 
//get the ECID and pass it to the function 
var mcID = visitor.getMarketingCloudVisitorID(useMarketingCloudID)
```

>[!TIP]
>
>如果您是Analytics客戶，請一併檢查Analytics ID，並將其傳送至您的函式。 例如，將隱藏表單元素中的訪客 ID 傳遞至使用資料插入 API 的伺服器端時，您會想要有兩個識別碼。 在此情況下，您應該收集並傳回ECID與Analytics訪客ID。 請參閱[取得 Analytics 訪客 ID](../../library/get-set/getanalyticsvisitorid.md)。

