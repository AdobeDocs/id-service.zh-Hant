---
description: setCustomerIDs 會設定 1 或多個機碼值組，定義客戶 ID 及其驗證狀態。
keywords: 訪客 ID 服務
title: setCustomerIDs
exl-id: 8fc549d3-2a6f-4214-bb0d-3e0bc1501ce2
TQID: https://experienceleague.adobe.com/PY-2KQSxqIV1xygQwSduPuq-YeYt5tY-UMGh4sRSZNM
product_v2: id: e1971122-7081-4556-9222-8a31bd71800c
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554id: c66ffd68-0f65-42bb-aa23-b4020f12e0bdid: f8a45b24-4be7-4f1b-909b-60d06b483a20id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
source-git-commit: 09ee359440c122702a6ce83708c98af3862c9cc9
workflow-type: tm+mt
source-wordcount: 63
ht-degree: 100%

---

# setCustomerIDs{#setcustomerids}

setCustomerIDs 會設定 1 或多個機碼值組，定義客戶 ID 及其驗證狀態。

**語法:** `visitor.setCustomerIDs()`

如下列程式碼範例所示，您可以設定單一或多個 ID。 如需詳細資訊和範例，請參閱[客戶 ID 和驗證狀態](../../reference/authenticated-state.md)。

```js
// Single ID with a single authentication state 
visitor.setCustomerIDs({ 
    "userid":{ 
        "id":"67312378756723456", 
        "authState":Visitor.AuthState.AUTHENTICATED 
    } 
}); 
 
//Multiple IDs with a single authentication state 
visitor.setCustomerIDs({ 
    "userid":{ 
        "id":"67312378756723456", 
        "authState":Visitor.AuthState.AUTHENTICATED 
    }, 
    "dpuuid":"550e8400-e29b-41d4-a716-446655440000" 
});
```

