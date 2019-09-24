---
description: setCustomerIDs 會設定 1 或多個機碼值組，定義客戶 ID 及其驗證狀態。
keywords: ID 服務
seo-description: setCustomerIDs 會設定 1 或多個機碼值組，定義客戶 ID 及其驗證狀態。
seo-title: setCustomerIDs
title: setCustomerIDs
uuid: 4f960f98-cec2-4db6-84ea-0259e2128ea2
translation-type: tm+mt
source-git-commit: 21fb12b817b7c8cd34e6022ca6c188229228d1df

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

