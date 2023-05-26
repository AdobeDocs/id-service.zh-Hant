---
description: 此設定可讓您在使用 appendSupplementalDataIDTo helper 函數將某個頁面的 Supplemental Data ID (SDID) 傳遞給另一個頁面時，覆寫該 ID 的預設到期間隔。根據預設，接收頁面上的 ID 服務程式碼有 30 秒的時間可取得參考頁面所傳送的 URL 中的 SDID。如果接收頁面上的 ID 服務程式碼無法在少於 30 秒的情況下擷取 SDID，它會要求新的 SDID。此功能主要適用於需要在不同頁面之間傳遞 SDID 以及想要控制此逾時間隔的 A4T 客戶。
keywords: ID 服務
title: sdidParamExpiry
exl-id: 5458ffa5-03d1-4c52-907d-c50fe00ce35d
source-git-commit: 06e935a4ba4776baa900d3dc91e294c92b873c0f
workflow-type: tm+mt
source-wordcount: '257'
ht-degree: 100%

---

# sdidParamExpiry{#sdidparamexpiry}

此設定可讓您在使用 appendSupplementalDataIDTo helper 函數將某個頁面的 Supplemental Data ID (SDID) 傳遞給另一個頁面時，覆寫該 ID 的預設到期間隔。根據預設，接收頁面上的 ID 服務程式碼有 30 秒的時間可取得參考頁面所傳送的 URL 中的 SDID。如果接收頁面上的 ID 服務程式碼無法在少於 30 秒的情況下擷取 SDID，它會要求新的 SDID。此功能主要適用於需要在不同頁面之間傳遞 SDID 以及想要控制此逾時間隔的 A4T 客戶。

**覆寫 SDID 逾時**

如果您需要變更預設的 SDID 逾時，請使用下列語法將 `sdidParamExpiry` 新增至 `Visitor.getInstance` 函數:

**語法：**` sdidParamExpiry: *`以秒為單位的時間`*`

**程式碼範例**

在設定您的 ID 服務程式碼之後，它可能與這個範例類似。此範例將 SDID 逾時設定為 15 秒。此設定適用於 [appendSupplementalDataIDTo](../../library/get-set/appendsupplementaldataidto.md#reference-65d09de6fde0418f8c62fa79304a755d) helper 方法。

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
