---
description: 此 helper 方法可讓您將 Supplemental Data ID (SDID) 當做查詢字串參數附加到重新導向 URL 中。 當使用 A4T 而且您需要在不同頁面保存 SDID 並將這些不同造訪拼貼在一起時，此方法會很實用。 若要使用此函式，您必須先實作訪客ID服務，且來源和目的地網域都使用相同的IMS組織ID。
keywords: 訪客 ID 服務
title: appendSupplementalDataIDTo
exl-id: 7f0e7fca-4551-4165-a12b-c7e5514d6818
TQID: https://experienceleague.adobe.com/oR2LCiVk5N-Xnt3wTOKMt7UYFXzwEGFwJpKoz-ikzh8
product_v2:
  - id: e1971122-7081-4556-9222-8a31bd71800c
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: f8a45b24-4be7-4f1b-909b-60d06b483a20
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
source-git-commit: 09ee359440c122702a6ce83708c98af3862c9cc9
workflow-type: tm+mt
source-wordcount: 354
ht-degree: 61%

---

# appendSupplementalDataIDTo{#appendsupplementaldataidto}

此 helper 方法可讓您將 Supplemental Data ID (SDID) 當做查詢字串參數附加到重新導向 URL 中。 當使用 A4T 而且您需要在不同頁面保存 SDID 並將這些不同造訪拼貼在一起時，此方法會很實用。 若要使用此函式，您必須先實作訪客ID服務，且來源和目的地網域都使用相同的IMS組織ID。

內容:

<ul class="simplelist"> 
 <li> <a href="../../library/get-set/appendsupplementaldataidto.md#section-cbb0b2f73bcc418386796c24c01b2365" format="dita" scope="local"> 語法與程式碼範例 </a> </li> 
 <li> <a href="../../library/get-set/appendsupplementaldataidto.md#section-dbe02d7ff6bd4ad1a2a26bf9cff54fa4" format="dita" scope="local"> 範例輸出 </a> </li> 
 <li> <a href="../../library/get-set/appendsupplementaldataidto.md#section-cbb0b2f73bcc418386796c24c01b2365" format="dita" scope="local"> 語法與程式碼範例 </a> </li> 
 <li> <a href="../../library/get-set/appendsupplementaldataidto.md#section-99946715cefa4acc95200b093db5297e" format="dita" scope="local"> 使用 sdidParamExpiry 變更 SDID 逾時 </a> </li> 
</ul>

## 語法與程式碼範例 {#section-cbb0b2f73bcc418386796c24c01b2365}

**語法:** `appendSupplementalDataIDTo( *`URL`*, *`SDID`*)`

**程式碼範例**

```js
var visitor = Visitor.getInstance("INSERT-IMS-ORG-ID-HERE"); 

//Get current supplemental data id
var theCurrentSDID = visitor._supplementalDataIDCurrent ? visitor._supplementalDataIDCurrent : "";

//Call helper method to append SDID to the Page B URL from Page A 
var pageB = "www.domain.com/pageB"; 
var pageBWithSdid = visitor.appendSupplementalDataIDTo(pageB, theCurrentSDID));
```

## 範例輸出 {#section-dbe02d7ff6bd4ad1a2a26bf9cff54fa4}

如下所示，URL在呼叫接收頁面時，重新導向會包含訪客的SDID、您的IMS組織ID以及UNIX時間戳記。

<ul class="simplelist"> 
 <li> <span class="codeph"> www.domain.com/pageB?adobe_mc_sdid=SDID=7996F0B028999505-13DA591039D6226|MCORGID=123456789@AdobeOrg|TS=1498569322 </span> </li> 
</ul>

## 使用 sdidParamExpiry 變更 SDID 逾時 {#section-99946715cefa4acc95200b093db5297e}

使用 `appendSupplementalDataIDTo` 協助函數將該 ID 從一個頁面傳至另一個頁面時，[sdidParamExpiry](../../library/function-vars/sdidparamexpiry.md#reference-cef3fd03c43b4772b2422e220b40a458) 設定可讓您變更預設的 SDID 過期時間間隔。 根據預設，接收頁面上的訪客ID服務程式碼有30秒的時間可取得參考頁面所傳送的URL中的SDID。 如果接收頁面上的訪客ID服務程式碼無法在30秒內擷取SDID，它會要求新的SDID。 此功能主要適用於需要在不同頁面之間傳遞 SDID 以及想要控制此逾時間隔的 A4T 客戶。

如果您需要變更預設的 SDID 逾時，請使用下列語法將 `sdidParamExpiry` 新增至 `Visitor.getInstance` 函數:

**語法：**`sdidParamExpiry: *`以秒為單位的時間`*`

**程式碼範例**

設定您的訪客ID服務程式碼之後，它可能與這個範例類似。 此範例將 SDID 逾時設定為 15 秒。

```js
var visitor = Visitor.getInstance ("INSERT-IMS-ORG-ID-HERE",{ 
   ... 
   //Change the default SDID timeout to 15 seconds 
   sdidParamExpiry: 15 
}); 
 
//Get current supplemental data id
var theCurrentSDID = visitor._supplementalDataIDCurrent ? visitor._supplementalDataIDCurrent : "";

//Call helper method to append SDID to the Page B URL from Page A 
var pageB = "www.domain.com/pageB"; 
var pageBWithSdid = visitor.appendSupplementalDataIDTo(pageB, theCurrentSDID)); 
```

