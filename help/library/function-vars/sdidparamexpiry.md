---
description: 此設定可讓您使用 appendSupplementalDataIDTo 協助函數從將該 ID 從一個頁面傳至另一個頁面時，覆寫預設的增補資料 ID (SDID) 過期時間間隔。依預設，接收頁面的 ID 服務程式碼有 30 秒的時間，取得透過所述頁面傳送的 URL 提供的 SDID。如果接收頁面的 ID 服務程式碼無法在 30 秒內擷取 SDID，則會要求新的 SDID。此功能主要適用於需要從某一頁面傳遞 SDID 至另外一個頁面，同時還要控制逾時時間間隔的 A4T 客戶。
keywords: ID 服務
seo-description: 此設定可讓您使用 appendSupplementalDataIDTo 協助函數從將該 ID 從一個頁面傳至另一個頁面時，覆寫預設的增補資料 ID (SDID) 過期時間間隔。依預設，接收頁面的 ID 服務程式碼有 30 秒的時間，取得透過所述頁面傳送的 URL 提供的 SDID。如果接收頁面的 ID 服務程式碼無法在 30 秒內擷取 SDID，則會要求新的 SDID。此功能主要適用於需要從某一頁面傳遞 SDID 至另外一個頁面，同時還要控制逾時時間間隔的 A4T 客戶。
seo-title: sdidParamExpiry
title: sdidParamExpiry
uuid: cdaf7e2d-b196-4c70-936d-8a98191cbb85
translation-type: ht
source-git-commit: bc5c81455023e22e64877bb861dfe141e158599c

---


# sdidParamExpiry{#sdidparamexpiry}

此設定可讓您使用 appendSupplementalDataIDTo 協助函數從將該 ID 從一個頁面傳至另一個頁面時，覆寫預設的增補資料 ID (SDID) 過期時間間隔。依預設，接收頁面的 ID 服務程式碼有 30 秒的時間，取得透過所述頁面傳送的 URL 提供的 SDID。如果接收頁面的 ID 服務程式碼無法在 30 秒內擷取 SDID，則會要求新的 SDID。此功能主要適用於需要從某一頁面傳遞 SDID 至另外一個頁面，同時還要控制逾時時間間隔的 A4T 客戶。

**覆寫 SDID 逾時**

如果您需要變更預設的 SDID 逾時，請使用下列語法將 `sdidParamExpiry` 新增至 `Visitor.getInstance` 函數:

**語法:** ` sdidParamExpiry: *`以秒為單位的時間`*`

**程式碼範例**

設定您的 ID 服務程式碼後，看起來可能會近似於此範例。此範例將 SDID 逾時設為 15 秒。此設定可搭配[appendSupplementalDataIDTo](../../library/get-set/appendsupplementaldataidto.md#reference-65d09de6fde0418f8c62fa79304a755d) 協助方法使用。

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

