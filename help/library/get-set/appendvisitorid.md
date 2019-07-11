---
description: 當瀏覽器封鎖第三方 Cookie 時，此函數可讓您跨網域共用訪客的 Experience Cloud ID。若要使用此函數，您必須先實作 ID 服務，且擁有來源和目的地的網域。適用於 VisitorAPI.js 1.7.0 版或更新版本。
keywords: ID 服務
seo-description: 當瀏覽器封鎖第三方 Cookie 時，此函數可讓您跨網域共用訪客的 Experience Cloud ID。若要使用此函數，您必須先實作 ID 服務，且擁有來源和目的地的網域。適用於 VisitorAPI.js 1.7.0 版或更新版本。
seo-title: appendVisitorIDsTo (跨網域追蹤)
title: appendVisitorIDsTo (跨網域追蹤)
uuid: 06b453ee-73c5-4625-82d9-877ad2b4f702
translation-type: ht
source-git-commit: 3e7b49564938527e1b6bca3a5fbaf9eb141d2e06

---


# appendVisitorIDsTo (跨網域追蹤){#appendvisitoridsto-cross-domain-tracking}

當瀏覽器封鎖第三方 Cookie 時，此函數可讓您跨網域共用訪客的 Experience Cloud ID。若要使用此函數，您必須先實作 ID 服務，且擁有來源和目的地的網域。適用於 VisitorAPI.js 1.7.0 版或更新版本。

內容:

<ul class="simplelist"> 
 <li> <a href="../../library/get-set/appendvisitorid.md#section-7251d88befd440b4b79520e33c5aa44a" format="dita" scope="local"> 在第三方 Cookie 遭到瀏覽器封鎖時跨網域追蹤訪客 </a> </li> 
 <li> <a href="../../library/get-set/appendvisitorid.md#section-62d55f7f986542b0b9238e483d50d7b0" format="dita" scope="local"> 附加訪客 ID 程式碼範例 </a> </li> 
 <li> <a href="../../library/get-set/appendvisitorid.md#section-168e313df6054af0a7e27b9fa0d69640" format="dita" scope="local"> 動態標籤管理 (DTM) 以及 SDK 支援 </a> </li> 
</ul>

## 在第三方 Cookie 遭到瀏覽器封鎖時跨網域追蹤訪客 {#section-7251d88befd440b4b79520e33c5aa44a}

當使用者造訪您的網站，ID 服務會將第一方和第三方 Cookie 寫入瀏覽器 (請參閱 [Cookie 和 Experience Cloud ID 服務](../../introduction/cookies.md))。第一方 Cookie 包含 MID，即為一組該訪客專用的個別的 ID。第三方 Cookie 包含另一組由 ID 服務用來產生 MID 的 ID。若瀏覽器封鎖此第三方 Cookie，ID 服務將無法:

* 在訪客導覽至其他網域時，針對該網站訪客重新產生個別 ID。
* 跨不同網域追蹤屬於貴組織的訪客。

為解決此問題，請實作 ` Visitor.appendVisitorIDsTo( *``*)`。就算訪客的瀏覽器封鎖第三方 Cookie，此屬性仍可讓 ID 服務在不同的網域間追蹤網站訪客。其運作方式類似這樣:

* 訪客瀏覽至您的其他網域時，` Visitor.appendVisitorIDsTo( *`url`*)` 會附加 MID 作為 URL 重新導向 (從原始網域重新導向至目的地網域) 中的查詢參數。
* 目的地網域上的 ID 服務程式碼會從 URL 提取 MID，而非傳送要求給 Adobe 索取該訪客的 ID。此要求包含第三方 Cookie ID，而該 ID 在此案件中無法使用。
* 目的地頁面上的 ID 服務程式碼使用傳入的 MID 來追蹤訪客。

請參閱程式碼範例以取得詳細資料。

## 附加訪客 ID 程式碼範例 {#section-62d55f7f986542b0b9238e483d50d7b0}

以下範例可以幫助您開始使用 ` Visitor.appendVisitorIDsTo( *`url`*)`。如果妥善實作，您的 JavaScript 程式碼看起來可能類似於下列範例。

```js
//Code on Domain A 
var destinationURL = "www.destination.com"; 
 
//Call the ID service 
var visitor = Visitor.getInstance(...); 
 
//Append visitor IDs to the destination URL 
var destinationURLWithVisitorIDs = visitor.appendVisitorIDsTo(destinationURL); 
     //Result of appendVisitorIDsTo includes destination URL, Experience Cloud ID (MCMID), and Analytics ID (MCAID) 
     "www.destination.com?adobe_mc=MCMID=1234|MCAID=5678 
<draft-comment>
  |TS=123675879 
</draft-comment>" 
 
//Redirect to the destination
```

## 動態標籤管理 (DTM) 以及 SDK 支援 {#section-168e313df6054af0a7e27b9fa0d69640}

<table id="table_6E7152B4FD2B4C4D8C9477C68204C4FF"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> 支援 </th> 
   <th colname="col2" class="entry"> 請參閱 </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <b>DTM</b> </p> </td> 
   <td colname="col2"> <p> <a href="/content/help/tw/zh-Hant/dtm/kb/how-to-set-marketing-cloud-id-service-helper-function-in-adobe-d.html" format="https" scope="external"> 在 DTM 中，設定 appendVisitorIDTo 函數 </a> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>SDK</b> </p> </td> 
   <td colname="col2"> 
    <ul id="ul_9D7933FF68EE4C71BAE999B3747F8398"> 
     <li id="li_9036C76AAECC4E639C23020C0C9F2AF8"> <a href="https://marketing.adobe.com/resources/help/zh_TW/mobile/android/mc_methods.html" format="https" scope="external"> Android ID 服務方法 </a> </li> 
     <li id="li_E49D357905584674BFDFE348345B3849"> <a href="https://marketing.adobe.com/resources/help/zh_TW/mobile/ios/mc_methods.html" format="https" scope="external"> iOS ID 服務方法 </a> </li> 
    </ul> </td> 
  </tr> 
 </tbody> 
</table>

