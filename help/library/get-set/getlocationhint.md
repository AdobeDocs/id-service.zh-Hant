---
description: 傳回Experience Cloud Identity Service地區ID。地區 ID (或位置點擊) 是代表特定 ID 服務資料中心之地理位置的數字識別碼。您需要地區 ID 才能對 Audience Manager 進行伺器服端 API 呼叫。
keywords: ID 服務
seo-description: 傳回Experience Cloud Identity Service地區ID。地區 ID (或位置點擊) 是代表特定 ID 服務資料中心之地理位置的數字識別碼。您需要地區 ID 才能對 Audience Manager 進行伺器服端 API 呼叫。
seo-title: getLocationHint
title: getLocationHint
uuid: cdc312b7-d270-4a5c-a2bb-0fbb37f1e2f4
translation-type: tm+mt
source-git-commit: e6d65f1bfed187d7440512e8f3c2de0550506c95

---


# getLocationHint{#getlocationhint}

傳回Experience Cloud Identity Service地區ID。地區 ID (或位置點擊) 是代表特定 ID 服務資料中心之地理位置的數字識別碼。您需要地區 ID 才能對 Audience Manager 進行伺器服端 API 呼叫。

**語法:** ` var *`變數名稱`* = visitor.getLocationHint()`

如需關於地區 ID 和對應位置的清單，請參閱 [DCS 地區 ID、位置與主機名稱](https://marketing.adobe.com/resources/help/en_US/aam/dcs-regions.html)。

**程式碼範例**

位置點擊函數會從 AMCV Cookie 讀取地區 ID。如果 AMCV Cookie 中已設定地區 ID，則會立即進行回撥。如果尚未設定地區 ID，函數會先等候伺服器的回應，然後再傳遞地區 ID 給回撥。您的程式碼看起來可能類似於下列範例。

```js
//callback function 
var callback = function ( 
<i>region ID here</i>){ 
//do whatever your function does with the region ID 
}; 
 
//Get the region ID 
visitor.getLocationHint(callback, true); 
```

