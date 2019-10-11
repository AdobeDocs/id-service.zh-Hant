---
description: getMarketingCloudVisitorID 傳回 Experience Cloud 訪客 ID。
keywords: ID 服務
seo-description: getMarketingCloudVisitorID 傳回 Experience Cloud 訪客 ID。
seo-title: getMarketingCloudVisitorID
title: getMarketingCloudVisitorID
uuid: 93e16220-b5b3-4d81-9189-30031bc15129
translation-type: ht
source-git-commit: 4a5fbc971dc950c65e5c8f92dffdfe5dde528b54

---


# getMarketingCloudVisitorID{#getmarketingcloudvisitorid}

getMarketingCloudVisitorID 傳回 Experience Cloud 訪客 ID。

**語法:** ` var *`變數名稱`* = visitor.getMarketingCloudVisitorID()`

此方法通常用於需要讀取訪客 ID 的自訂解決方案。標準實作不會使用此方法。`getMarketingCloudVisitorID` 也會使用回呼函數讀取 [!DNL Analytics] ID，並將其帶入您的系統或應用程式。

```js
//callback function 
var useMarketingCloudID = function(id){ 
     //whatever your function does with the Experience Cloud ID 
}; 
 
//get the Experience Cloud ID and pass it to the function 
var mcID = visitor.getMarketingCloudVisitorID(useMarketingCloudID)
```

>[!TIP]
>
>如果您是 [!DNL Analytics] 客戶，請一併檢查 [!DNL Analytics] ID，並將其傳送至您的函數。例如，將隱藏表單元素中的訪客 ID 傳遞至使用資料插入 API 的伺服器端時，您會想要有兩個識別碼。在此情況下，您應該收集並傳回 [!DNL Experience Cloud] 與 [!DNL Analytics] 訪客 ID。請參閱[取得 Analytics 訪客 ID](../../library/get-set/getanalyticsvisitorid.md)。

