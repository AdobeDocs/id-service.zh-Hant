---
description: 這些設定可讓實作於 iFrame 及上層頁面的不同 ID 服務代碼執行個體互相通訊。這兩個設定專為協助解決 2 個特定使用案例問題而設計。在特定使用案例中，您可能需要控制上層頁面/網域，並擁有載入您所控制網域之 iFrame 的 ID 服務代碼。VisitorAPI.js 程式碼 2.2 以上版本皆已提供這兩種設定。
keywords: ID 服務
seo-description: 這些設定可讓實作於 iFrame 及上層頁面的不同 ID 服務代碼執行個體互相通訊。這兩個設定專為協助解決 2 個特定使用案例問題而設計。在特定使用案例中，您可能需要控制上層頁面/網域，並擁有載入您所控制網域之 iFrame 的 ID 服務代碼。VisitorAPI.js 程式碼 2.2 以上版本皆已提供這兩種設定。
seo-title: whitelistParentDomain 及 whitelistIframeDomains
title: whitelistParentDomain 及 whitelistIframeDomains
uuid: 6b66a4d0-fea2-4d98-963e-0c4f4ab1efb6
translation-type: tm+mt
source-git-commit: f7f23d89649a888f5e9d8c94526b550fbda7045b

---


# whitelistParentDomain 及 whitelistIframeDomains{#whitelistparentdomain-and-whitelistiframedomains}

這些設定可讓實作於 iFrame 及上層頁面的不同 ID 服務代碼執行個體互相通訊。這兩個設定專為協助解決 2 個特定使用案例問題而設計。在特定使用案例中，您可能需要控制上層頁面/網域，並擁有載入您所控制網域之 iFrame 的 ID 服務代碼。VisitorAPI.js 程式碼 2.2 以上版本皆已提供這兩種設定。

內容:

<ul class="simplelist"> 
 <li> <a href="../../library/function-vars/whitelistdomain.md#section-f645198bbaba4fba8961acb6e88d1470" format="dita" scope="local"> 語法 </a> </li> 
 <li> <a href="../../library/function-vars/whitelistdomain.md#section-09d0049fe88a473baa69d404c50bf8ae" format="dita" scope="local"> 程式碼範例 </a> </li> 
 <li> <a href="../../library/function-vars/whitelistdomain.md#section-fc2eeb93546b406fae3b102dbcd11de7" format="dita" scope="local"> 使用案例 </a> </li> 
 <li> <a href="../../library/function-vars/whitelistdomain.md#section-2b1ce31fab034e1ca0f6b1c3cc57a6e2" format="dita" scope="local"> 設定安全與安全性 </a> </li> 
 <li> <a href="../../library/function-vars/whitelistdomain.md#section-30c6a9f4dcdc4265a1149260b97cc057" format="dita" scope="local"> 支援的訪客 API 方法 </a> </li> 
</ul>

## 語法 {#section-f645198bbaba4fba8961acb6e88d1470}

使用此程式碼時需要這兩個設定元素。

<table id="table_237108A4D40F4AAC981D0060BA68F881"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> 設定語法 </th> 
   <th colname="col2" class="entry"> 說明 </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> whitelistParentDomain: " <span class="varname"> 上層頁面的網域名稱 </span>" </span> </p> </td> 
   <td colname="col2"> <p>接受單一網域名稱以字串形式傳入。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> whitelistIframeDomains: [ <span class="varname"> "iFrame 網域","iFrame 網域","iFrame 網域" </span>] </span> </p> </td> 
   <td colname="col2"> <p>接受一個或多個 iFrame 網域名稱以陣列形式傳入。 </p> </td> 
  </tr> 
 </tbody> 
</table>

## 程式碼範例 {#section-09d0049fe88a473baa69d404c50bf8ae}

您的設定 [!UICONTROL ID 服務]程式碼看起來可能類似於此範例。

```js
//Instantiate Visitor 
var visitor = Visitor.getInstance("Insert Experience Cloud Organization ID here",{ 
 ... 
 //Add parent page domain name and iFrame domain names 
 whitelistParentDomain: "parentpageA.com", 
 whitelistIframeDomains: ["iFrameDomain1.com","iFrameDomain2.com"], 
 ... 
 } 
);
```

## 使用案例 {#section-fc2eeb93546b406fae3b102dbcd11de7}

當瀏覽器封鎖第三方 Cookie 或下列任一情況發生時，這些設定有助於解決設定 ID 服務 Cookie 和指派訪客 ID 的問題:

* 您能夠或不能夠控制上層頁面/網域。
* ID 服務程式碼並未安裝於上層網頁，但已在 iFrame 中施實。

>[!TIP]
>
>You may also want to implement these configurations when you're serving video in an iFrame with [Video Heartbeat](https://marketing.adobe.com/resources/help/en_US/sc/appmeasurement/hbvideo/). 影片心率需要有 ID 服務 ID (MID) 才能正常運作。

**使用案例 1: 在 iFrame 和上層頁面實作瀏覽器封鎖第三方 Cookie 及 ID 服務**

<table id="table_B479AA96DBE64685A253A6DF98D81B31"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> 使用案例元素 </th> 
   <th colname="col2" class="entry"> 說明 </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <b>條件</b> </p> </td> 
   <td colname="col2"> <p>這會使用包含下列條件的案例: </p> <p> 
     <ul id="ul_DC748846585745B0AB74398D82BDA53A"> 
      <li id="li_6E04CF0B6A204B4D8856656B0C9EF2A5">A 公司在其首頁中實作了 ID 服務。 </li> 
      <li id="li_B53AE0F0C69844E7B6C4D3464C57883B">A 公司在其首頁的 iFrame 中實作了 ID 服務。 </li> 
      <li id="li_07E0A6D7BEB140E4B9FB6C7B9629B860">A 公司擁有上層頁面和 iFrame，而且兩處均已實作 ID 服務。 </li> 
      <li id="li_76967BD69DDB40A8A9C915DADC58AC62">客戶透過會封鎖第三方 Cookie 的瀏覽器載入上層頁面。 </li> 
     </ul> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>結果</b> </p> </td> 
   <td colname="col2"> <p>基於上述條件，ID 服務會: </p> <p> 
     <ul id="ul_12356701501E40DFA57903494FFE58F7"> 
      <li id="li_B57EDF1B0762486F95FA6526C047390C">在上層頁面正常運作。ID 服務會要求並設定 AMCV Cookie，並會將唯一 ID 指派給網站訪客。 </li> 
      <li id="li_BA9F42C759E747EAAE14DD3FBB6130A5">在 iFrame 中無法運作。因為瀏覽器會將 iFrame 視為第三方網域，因而防止 ID 服務設定 AMCV Cookie。 </li> 
     </ul> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>解決方法</b> </p> </td> 
   <td colname="col2"> <p>藉由這些白名單設定來修改 iFrame 中的 ID 服務 <span class="codeph">Visitor.getInstance</span> 函數。在程式碼中指定上層網域和子網域。這些設定可讓 iFrame 中的 ID 服務程式碼檢查訪客 ID 的上層頁面 ID 服務程式碼。 </p> <p>如果 iFrame 的 ID 服務程式碼沒有收到回應的上層頁面，這些設定便會產生本機訪客 ID。 </p> </td> 
  </tr> 
 </tbody> 
</table>

**使用案例 2: 向您無法控制或不使用 ID 服務的上層頁內嵌 iFrame 中要求 ID**

<table id="table_1F21710F9D5F493BA6BA5974F2966DF4"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> 使用案例元素 </th> 
   <th colname="col2" class="entry"> 說明 </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <b>條件</b> </p> </td> 
   <td colname="col2"> <p>這會使用包含下列條件的案例: </p> <p> 
     <ul id="ul_356E8FB0B1D14F46A844FE5281967E28"> 
      <li id="li_1285D945361842268B46FB492A3B5AA5">A 公司並未使用 ID 服務。 </li> 
      <li id="li_880D6D473F8342FF9BB49FCE111FD61A">A 公司在頁面中載入 iFrame。此 iFrame 由 B 公司擁有，並會在 A 公司以外的另一個網域載入。 </li> 
      <li id="li_7988F0272B094FE0B398006AD4E6F81B">瀏覽器封鎖第三方 Cookie。 </li> 
     </ul> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>結果</b> </p> </td> 
   <td colname="col2"> <p>基於上述條件，ID 服務會: </p> <p> 
     <ul id="ul_A92D90896E5A42C5804AC5CE83E8EB25"> 
      <li id="li_9734EA9C5D9D4F908DE783188C9E5530">在 iFrame 中無法運作。因為瀏覽器會將 iFrame 視為第三方網域，因而防止 ID 服務設定 AMCV Cookie。 </li> 
      <li id="li_3F4BE9048E774902A867D67E5A80674D">由於 A 公司並未使用此服務，因此無法透過上層頁面取得訪客 ID。 </li> 
     </ul> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>解決方法</b> </p> </td> 
   <td colname="col2"> <p>藉由這些白名單設定來修改 iFrame 中的 ID 服務 <span class="codeph">Visitor.getInstance</span> 函數。在程式碼中指定上層網域和子網域。這些設定可讓 iFrame 中的 ID 服務程式碼檢查訪客 ID 的上層頁面 ID 服務程式碼。 </p> <p>如果 iFrame 的 ID 服務程式碼沒有收到回應的上層頁面，這些設定便會產生本機訪客 ID。 </p> </td> 
  </tr> 
 </tbody> 
</table>

## 設定安全與安全性 {#section-2b1ce31fab034e1ca0f6b1c3cc57a6e2}

您可以安全地實作這些設定，因為:

* 在上層網域和 iFrame 網域中實作的 ID 服務必須使用相同的組織 ID。如果上層或 iFrame 中的組織 ID 不同，這些白名單設定便無法運作。
* 這些設定只會與程式碼所指定的網域和 iFrames 通訊。
* iFrame 與上層頁面之間的通訊會採用特定的格式。如果上層頁面的 ID 服務沒有接收到採用預期格式的要求，則此共用程序就會失敗。

## 支援的訪客 API 方法 {#section-30c6a9f4dcdc4265a1149260b97cc057}

實作這些白名單設定時，ID 服務支援有限的公用 API 方法集。支援的方法會依上述使用案例而有所不同。

<table id="table_0FF9E529FD1C43A8A3B2B0D789C8E83C"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> 使用案例 </th> 
   <th colname="col2" class="entry"> 支援的方法 </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <b>案例 1</b> </p> </td> 
   <td colname="col2"> <p> 
     <ul id="ul_99FAC8608F4C4B39805EEAA6297DB771"> 
      <li id="li_B13F6C4119F44F17963794B1E2046B1F"> <span class="codeph"> getMarketingCloudID </span> </li> 
      <li id="li_9C1B5C00A17F467CAB7EFE5F0D040777"> <span class="codeph"> getAudienceManagerLocationHint </span> </li> 
      <li id="li_30D4608F4C3849659FCBA97D88A10F0C"> <span class="codeph"> getAudienceManagerBlob </span> </li> 
      <li id="li_BA359596C80147EEA89CABCE83F123CA"> <span class="codeph"> getSupplementalDataID </span> </li> 
      <li id="li_26774089B6854CD6A3216043B6EEA01B"> <span class="codeph"> getCustomerIDs </span> </li> 
     </ul> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>案例 2</b> </p> </td> 
   <td colname="col2"> <p> 
     <ul id="ul_CCAD7E362E7F4DAB9D5C3E166EEE6BDD"> 
      <li id="li_1F0B006BAD044ECBA5604625DE411E84"> <span class="codeph"> getSupplementalDataID </span> </li> 
      <li id="li_C6022223C8314B9C923202207C7472EA"> <span class="codeph"> getMarketingCloudVisitorID </span> </li> 
     </ul> </p> </td> 
  </tr> 
 </tbody> 
</table>

