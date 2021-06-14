---
description: setCustomerIDs 會設定 1 或多個機碼值組，定義客戶 ID 及其驗證狀態。
keywords: ID 服務
title: setCustomerIDs
exl-id: 8fc549d3-2a6f-4214-bb0d-3e0bc1501ce2
source-git-commit: 06e935a4ba4776baa900d3dc91e294c92b873c0f
workflow-type: ht
source-wordcount: '58'
ht-degree: 100%

---

# setCustomerIDs{#setcustomerids}

setCustomerIDs 會設定 1 或多個機碼值組，定義客戶 ID 及其驗證狀態。

**語法:** `visitor.setCustomerIDs()`

如下列程式碼範例所示，您可以設定單一或多個 ID。如需詳細資訊和範例，請參閱[客戶 ID 和驗證狀態](../../reference/authenticated-state.md)。

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
