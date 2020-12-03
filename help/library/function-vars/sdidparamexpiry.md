---
description: 此設定可讓您使用appendSupplementalDataIDTo協助函式，將該ID從一個頁面傳遞至另一個頁面時，覆寫預設的補充資料ID(SDID)過期間隔。 依預設，接收頁面上的ID服務程式碼有30秒可從轉介頁面傳送的URL取得SDID。 如果接收頁面上的ID服務程式碼在30秒內無法擷取SDID，則會要求新的SDID。 此功能主要適用於需要將SDID從一個頁面傳遞至另一個頁面，且想要控制此逾時間隔的A4T客戶。
keywords: ID Service
seo-description: 此設定可讓您使用appendSupplementalDataIDTo協助函式，將該ID從一個頁面傳遞至另一個頁面時，覆寫預設的補充資料ID(SDID)過期間隔。 依預設，接收頁面上的ID服務程式碼有30秒可從轉介頁面傳送的URL取得SDID。 如果接收頁面上的ID服務程式碼在30秒內無法擷取SDID，則會要求新的SDID。 此功能主要適用於需要將SDID從一個頁面傳遞至另一個頁面，且想要控制此逾時間隔的A4T客戶。
seo-title: sdidParamExpiry
title: sdidParamExpiry
uuid: cdaf7e2d-b196-4c70-936d-8a98191cbb85
translation-type: tm+mt
source-git-commit: bc5c81455023e22e64877bb861dfe141e158599c
workflow-type: tm+mt
source-wordcount: '355'
ht-degree: 7%

---


# sdidParamExpiry{#sdidparamexpiry}

此設定可讓您使用appendSupplementalDataIDTo協助函式，將該ID從一個頁面傳遞至另一個頁面時，覆寫預設的補充資料ID(SDID)過期間隔。 依預設，接收頁面上的ID服務程式碼有30秒可從轉介頁面傳送的URL取得SDID。 如果接收頁面上的ID服務程式碼在30秒內無法擷取SDID，則會要求新的SDID。 此功能主要適用於需要將SDID從一個頁面傳遞至另一個頁面，且想要控制此逾時間隔的A4T客戶。

**覆寫SDID逾時**

如果您需要變更預設的 SDID 逾時，請使用下列語法將 `sdidParamExpiry` 新增至 `Visitor.getInstance` 函數:

**語法:** ` sdidParamExpiry: *`以秒為單位的時間`*`

**程式碼範例**

設定好後，您的ID服務程式碼可能會看起來類似此範例。 此示例將SDID超時設定為15秒。 此組態可與 [appendSupplementalDataIDTo](../../library/get-set/appendsupplementaldataidto.md#reference-65d09de6fde0418f8c62fa79304a755d) helper方法搭配運作。

```js
var visitor = Visitor.getInstance ("Insert Experience Cloud organization ID here",{ 
   ... 
   //Change the default SDID timeout to 15 seconds 
   sdidParamExpiry: 15 
}); 
 
//Call helper method to append SDID to the Page B URL from Page A 
var pageB = "www.domain.com/pageB"; 
var pageBWithSdid = visitor.appendSupplementalDataIDTo(pageB, "67987653465787219"); 
```

