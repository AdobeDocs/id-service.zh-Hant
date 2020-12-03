---
description: 此輔助方法可讓您將補充資料ID(SDID)附加為查詢字串參數至重新導向URL。 當使用A4T時，這很有用，您需要將SDID從一個頁面保存到另一個頁面，並將這些個別的造訪連結在一起。 若要使用此函數，您必須先實作 ID 服務，且來源和目的地網域都使用相同的組織 ID。
keywords: ID Service
seo-description: 此輔助方法可讓您將補充資料ID(SDID)附加為查詢字串參數至重新導向URL。 當使用A4T時，這很有用，您需要將SDID從一個頁面保存到另一個頁面，並將這些個別的造訪連結在一起。 若要使用此函數，您必須先實作 ID 服務，且來源和目的地網域都使用相同的組織 ID。
seo-title: appendSupplementalDataIDTo
title: appendSupplementalDataIDTo
uuid: f3504d82-8da3-4971-818b-3df57df4ec2d
translation-type: tm+mt
source-git-commit: bc5c81455023e22e64877bb861dfe141e158599c
workflow-type: tm+mt
source-wordcount: '410'
ht-degree: 44%

---


# appendSupplementalDataIDTo{#appendsupplementaldataidto}

此輔助方法可讓您將補充資料ID(SDID)附加為查詢字串參數至重新導向URL。 當使用A4T時，這很有用，您需要將SDID從一個頁面保存到另一個頁面，並將這些個別的造訪連結在一起。 若要使用此函數，您必須先實作 ID 服務，且來源和目的地網域都使用相同的組織 ID。

內容:

<ul class="simplelist"> 
 <li> <a href="../../library/get-set/appendsupplementaldataidto.md#section-cbb0b2f73bcc418386796c24c01b2365" format="dita" scope="local"> 語法與程式碼範例 </a> </li> 
 <li> <a href="../../library/get-set/appendsupplementaldataidto.md#section-dbe02d7ff6bd4ad1a2a26bf9cff54fa4" format="dita" scope="local"> 範例輸出 </a> </li> 
 <li> <a href="../../library/get-set/appendsupplementaldataidto.md#section-cbb0b2f73bcc418386796c24c01b2365" format="dita" scope="local"> 語法與程式碼範例 </a> </li> 
 <li> <a href="../../library/get-set/appendsupplementaldataidto.md#section-99946715cefa4acc95200b093db5297e" format="dita" scope="local"> 使用 sdidParamExpiry 變更 SDID 逾時 </a> </li> 
</ul>

## 語法與程式碼範例 {#section-cbb0b2f73bcc418386796c24c01b2365}

**語法:** ` appendSupplementalDataIDTo( *`URL`*, *`SDID`*)`

**程式碼範例**

```js
var visitor = Visitor.getInstance ("Insert Experience Cloud organization ID here",{ 
   ... 
}); 
 
//Call helper method to append SDID to the Page B URL from Page A 
var pageB = "www.domain.com/pageB"; 
var pageBWithSdid = visitor.appendSupplementalDataIDTo(pageB, "67987653465787219");
```

## 範例輸出 {#section-dbe02d7ff6bd4ad1a2a26bf9cff54fa4}

如下所示，URL 在呼叫接收頁面時，重新導向會包含訪客的 SDID、您的組織 ID 以及 UNIX 時間戳記。

<ul class="simplelist"> 
 <li> <span class="codeph"> www.domain.com/pageB?adobe_mc_sdid=SDID=123|MCORGID=123456789@AdobeOrg|TS=1498569322 </span> </li> 
</ul>

## 使用 sdidParamExpiry 變更 SDID 逾時 {#section-99946715cefa4acc95200b093db5297e}

使用 `appendSupplementalDataIDTo` 協助函數將該 ID 從一個頁面傳至另一個頁面時，[sdidParamExpiry](../../library/function-vars/sdidparamexpiry.md#reference-cef3fd03c43b4772b2422e220b40a458) 設定可讓您變更預設的 SDID 過期時間間隔。依預設，接收頁面上的ID服務程式碼有30秒可從轉介頁面傳送的URL取得SDID。 如果接收頁面上的ID服務程式碼在30秒內無法擷取SDID，則會要求新的SDID。 此功能主要適用於需要將SDID從一個頁面傳遞至另一個頁面，且想要控制此逾時間隔的A4T客戶。

如果您需要變更預設的 SDID 逾時，請使用下列語法將 `sdidParamExpiry` 新增至 `Visitor.getInstance` 函數:

**語法:** ` sdidParamExpiry: *`以秒為單位的時間`*`

**程式碼範例**

設定好後，您的ID服務程式碼看起來可能類似此範例。 此示例將SDID超時設定為15秒。

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

