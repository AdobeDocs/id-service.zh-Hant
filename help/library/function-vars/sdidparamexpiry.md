---
description: 此設定可讓您在使用 appendSupplementalDataIDTo helper 函數將某個頁面的 Supplemental Data ID (SDID) 傳遞給另一個頁面時，覆寫該 ID 的預設過期間隔。 根據預設，接收頁面上的訪客ID服務程式碼有30秒的時間可取得參考頁面所傳送的URL中的SDID。 如果接收頁面上的訪客ID服務程式碼無法在30秒內擷取SDID，它會要求新的SDID。 此功能主要適用於需要在不同頁面之間傳遞 SDID 以及想要控制此逾時間隔的 A4T 客戶。
keywords: 訪客 ID 服務
title: sdidParamExpiry
exl-id: 5458ffa5-03d1-4c52-907d-c50fe00ce35d
TQID: https://experienceleague.adobe.com/PUHy-KpWKY0BQSMkKidwpLYES6FvME2EtKCbCpfMFrw
product_v2: id: e1971122-7081-4556-9222-8a31bd71800c
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554id: c66ffd68-0f65-42bb-aa23-b4020f12e0bdid: f8a45b24-4be7-4f1b-909b-60d06b483a20id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
source-git-commit: 09ee359440c122702a6ce83708c98af3862c9cc9
workflow-type: tm+mt
source-wordcount: 266
ht-degree: 57%

---

# sdidParamExpiry{#sdidparamexpiry}

此設定可讓您在使用 appendSupplementalDataIDTo helper 函數將某個頁面的 Supplemental Data ID (SDID) 傳遞給另一個頁面時，覆寫該 ID 的預設過期間隔。 根據預設，接收頁面上的訪客ID服務程式碼有30秒的時間可取得參考頁面所傳送的URL中的SDID。 如果接收頁面上的訪客ID服務程式碼無法在30秒內擷取SDID，它會要求新的SDID。 此功能主要適用於需要在不同頁面之間傳遞 SDID 以及想要控制此逾時間隔的 A4T 客戶。

**覆寫 SDID 逾時**

如果您需要變更預設的 SDID 逾時，請使用下列語法將 `sdidParamExpiry` 新增至 `Visitor.getInstance` 函數:

**語法：**`sdidParamExpiry: *`以秒為單位的時間`*`

**程式碼範例**

設定您的訪客ID服務程式碼後，它可能與這個範例類似。 此範例將 SDID 逾時設定為 15 秒。 此設定適用於 [appendSupplementalDataIDTo](../../library/get-set/appendsupplementaldataidto.md#reference-65d09de6fde0418f8c62fa79304a755d) helper 方法。

```js
var visitor = Visitor.getInstance ("INSERT-IMS-ORG-ID-HERE",{ 
   ... 
   //Change the default SDID timeout to 15 seconds 
   sdidParamExpiry: 15 
}); 
 
//Call helper method to append SDID to the Page B URL from Page A 
var pageB = "www.domain.com/pageB"; 
var pageBWithSdid = visitor.appendSupplementalDataIDTo(pageB, "67987653465787219"); 
```

