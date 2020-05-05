---
description: 傳回 Experience Cloud Identity 服務地區 ID。地區ID（或位置提示）是特定ID服務資料中心的地理位置的數值識別碼。 您需要地區ID，才能對Audience Manager進行伺服器端API呼叫。
keywords: ID Service
seo-description: 傳回 Experience Cloud Identity 服務地區 ID。地區ID（或位置提示）是特定ID服務資料中心的地理位置的數值識別碼。 您需要地區ID，才能對Audience Manager進行伺服器端API呼叫。
seo-title: getLocationHint
title: getLocationHint
uuid: cdc312b7-d270-4a5c-a2bb-0fbb37f1e2f4
translation-type: tm+mt
source-git-commit: d2bc0e7fedc4e48d51f5dad158f9f8bfcb0cb4f3

---


# getLocationHint{#getlocationhint}

傳回 Experience Cloud Identity 服務地區 ID。地區ID（或位置提示）是特定ID服務資料中心的地理位置的數值識別碼。 您需要地區ID，才能對Audience Manager進行伺服器端API呼叫。

**語法:** ` var *`變數名稱`* = visitor.getLocationHint()`

For a list of region IDs and corresponding locations, see [DCS Region IDs, Locations, and Host Names](https://docs.adobe.com/content/help/en/audience-manager/user-guide/api-and-sdk-code/dcs/dcs-api-reference/dcs-regions.html).

**程式碼範例**

位置提示函式會從AMCV Cookie讀取地區ID。 如果AMCV Cookie中已設定地區ID，則會立即進行回呼。 如果未設定地區ID，函式會先等待伺服器的回應，再將地區ID傳遞至回呼。 您的程式碼看起來可能類似於下列範例。

```js
//callback function 
var callback = function ( 
<i>region ID here</i>){ 
//do whatever your function does with the region ID 
}; 
 
//Get the region ID 
visitor.getLocationHint(callback, true); 
```

