---
description: 傳回 Experience Cloud Identity Service 地區 ID。地區 ID (或位置提示) 是特定 ID 服務資料中心之地理位置的數值識別碼。必須要有地區 ID，您才能對 Audience Manager 發出伺服器端 API 呼叫。
keywords: ID 服務
seo-description: 傳回 Experience Cloud Identity 服務地區 ID。地區 ID (或位置提示) 是特定 ID 服務資料中心之地理位置的數值識別碼。必須要有地區 ID，您才能對 Audience Manager 發出伺服器端 API 呼叫。
seo-title: getLocationHint
title: getLocationHint
uuid: cdc312b7-d270-4a5c-a2bb-0fbb37f1e2f4
exl-id: 0213f828-a985-4201-8a38-0a4b170ed057
translation-type: ht
source-git-commit: 4453ebf701ea2dc06e6093dd77be6eb0f3b2936e
workflow-type: ht
source-wordcount: '232'
ht-degree: 100%

---

# getLocationHint{#getlocationhint}

傳回 Experience Cloud Identity Service 地區 ID。地區 ID (或位置提示) 是特定 ID 服務資料中心之地理位置的數值識別碼。必須要有地區 ID，您才能對 Audience Manager 發出伺服器端 API 呼叫。

**語法：**` var *`變數名稱`* = visitor.getLocationHint()`

如需地區 ID 與對應位置的清單，請參閱 [DCS 地區 ID、位置與主機名稱](https://docs.adobe.com/content/help/zh-Hant/audience-manager/user-guide/api-and-sdk-code/dcs/dcs-api-reference/dcs-regions.html)。

**程式碼範例**

位置提示函數會從 AMCV Cookie 讀取地區 ID。如果 AMCV Cookie 中已設定地區 ID，則會立即進行回呼。若未設定地區 ID，則函數會先等待伺服器回應，再將地區 ID 傳至回呼。您的程式碼看起來可能類似於下列範例。

```js
//callback function 
var callback = function ( 
<i>region ID here</i>){ 
//do whatever your function does with the region ID 
}; 
 
//Get the region ID 
visitor.getLocationHint(callback, true); 
```
