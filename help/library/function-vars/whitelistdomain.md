---
description: 這些設定可讓實作於 iFrame 及上層頁面的不同 ID 服務代碼執行個體互相通訊。這些程式碼可協助您解決2種特定使用案例的問題，例如您可能控制或無法控制上層頁面／網域，且您在您控制之網域的iFrame中載入ID服務程式碼。 VisitorAPI.js程式碼2.2版或更新版本中提供這些功能。
keywords: ID Service
seo-description: 這些設定可讓實作於 iFrame 及上層頁面的不同 ID 服務代碼執行個體互相通訊。這些程式碼可協助您解決2種特定使用案例的問題，例如您可能控制或無法控制上層頁面／網域，且您在您控制之網域的iFrame中載入ID服務程式碼。 VisitorAPI.js程式碼2.2版或更新版本中提供這些功能。
seo-title: whitelistParentDomain 及 whitelistIframeDomains
title: whitelistParentDomain 及 whitelistIframeDomains
uuid: 6b66a4d0-fea2-4d98-963e-0c4f4ab1efb6
translation-type: tm+mt
source-git-commit: d2bc0e7fedc4e48d51f5dad158f9f8bfcb0cb4f3

---


# whitelistParentDomain 及 whitelistIframeDomains{#whitelistparentdomain-and-whitelistiframedomains}

這些設定可讓實作於 iFrame 及上層頁面的不同 ID 服務代碼執行個體互相通訊。這些程式碼可協助您解決2種特定使用案例的問題，例如您可能控制或無法控制上層頁面／網域，且您在您控制之網域的iFrame中載入ID服務程式碼。 VisitorAPI.js程式碼2.2版或更新版本中提供這些功能。

內容:

<ul class="simplelist"> 
 <li> <a href="../../library/function-vars/whitelistdomain.md#section-f645198bbaba4fba8961acb6e88d1470" format="dita" scope="local"> 語法 </a> </li> 
 <li> <a href="../../library/function-vars/whitelistdomain.md#section-09d0049fe88a473baa69d404c50bf8ae" format="dita" scope="local"> 程式碼範例 </a> </li> 
 <li> <a href="../../library/function-vars/whitelistdomain.md#section-fc2eeb93546b406fae3b102dbcd11de7" format="dita" scope="local"> 使用案例 </a> </li> 
 <li> <a href="../../library/function-vars/whitelistdomain.md#section-2b1ce31fab034e1ca0f6b1c3cc57a6e2" format="dita" scope="local"> 設定安全與安全性 </a> </li> 
 <li> <a href="../../library/function-vars/whitelistdomain.md#section-30c6a9f4dcdc4265a1149260b97cc057" format="dita" scope="local"> 支援的訪客 API 方法 </a> </li> 
</ul>

## 語法 {#section-f645198bbaba4fba8961acb6e88d1470}

使用此代碼時，需要兩個配置元素。

<table id="table_237108A4D40F4AAC981D0060BA68F881"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> 配置語法 </th> 
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

您設定的 [!UICONTROL ID 服務]程式碼看起來與此範例類似。

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

這些設定可協助解決當瀏覽器封鎖第三方Cookie且符合下列任一條件時，設定ID服務Cookie和指派訪客ID的問題：

* 您控制或不控制父頁面／網域。
* ID服務程式碼未安裝在父頁面上，但是會實作在iFrame中。

>[!TIP]
>
>當您在iFrame中使用視訊心率提供視訊時，您也可能想要實作這 [些設定](https://docs.adobe.com/content/help/zh-Hant/media-analytics/using/media-overview.html)。 視訊心率需要ID服務ID(MID)才能正常運作。

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
   <td colname="col2"> <p>此使用案例包含下列條件： </p> <p> 
     <ul id="ul_DC748846585745B0AB74398D82BDA53A"> 
      <li id="li_6E04CF0B6A204B4D8856656B0C9EF2A5">A 公司在其首頁中實作了 ID 服務。 </li> 
      <li id="li_B53AE0F0C69844E7B6C4D3464C57883B">A 公司在其首頁的 iFrame 中實作了 ID 服務。 </li> 
      <li id="li_07E0A6D7BEB140E4B9FB6C7B9629B860">A 公司擁有上層頁面和 iFrame，而且兩處均已實作 ID 服務。 </li> 
      <li id="li_76967BD69DDB40A8A9C915DADC58AC62">客戶將上層頁面載入封鎖第三方Cookie的瀏覽器。 </li> 
     </ul> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>結果</b> </p> </td> 
   <td colname="col2"> <p>基於這些條件，ID服務： </p> <p> 
     <ul id="ul_12356701501E40DFA57903494FFE58F7"> 
      <li id="li_B57EDF1B0762486F95FA6526C047390C">在父頁面上正常運作。 它會要求並設定AMCV Cookie，並指派唯一ID給網站訪客。 </li> 
      <li id="li_BA9F42C759E747EAAE14DD3FBB6130A5">在iFrame中無法運作。 這是因為瀏覽器會將iFrame視為協力廠商網域，並防止ID服務設定AMCV Cookie。 </li> 
     </ul> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>解決方法</b> </p> </td> 
   <td colname="col2"> <p>藉由這些白名單設定來修改 iFrame 中的 ID 服務 <span class="codeph">Visitor.getInstance</span> 函數。在程式碼中指定父網域和子網域。 這些設定可讓iFrame中的ID服務程式碼檢查父頁面上的ID服務程式碼，以取得訪客ID。 </p> <p>如果iFrame中的ID服務程式碼未收到回應父頁面，這些設定會產生本機訪客ID。 </p> </td> 
  </tr> 
 </tbody> 
</table>

**使用案例2: 從內嵌於父頁面的iFrame請求您未控制或未使用ID服務的ID**

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
   <td colname="col2"> <p>此使用案例包含下列條件： </p> <p> 
     <ul id="ul_356E8FB0B1D14F46A844FE5281967E28"> 
      <li id="li_1285D945361842268B46FB492A3B5AA5">公司A不使用ID服務。 </li> 
      <li id="li_880D6D473F8342FF9BB49FCE111FD61A">公司A會在頁面上載入iFrame。 此iFrame歸B公司所有，並載入到A公司以外的個別網域。 </li> 
      <li id="li_7988F0272B094FE0B398006AD4E6F81B">瀏覽器會封鎖協力廠商Cookie。 </li> 
     </ul> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>結果</b> </p> </td> 
   <td colname="col2"> <p>基於這些條件，ID服務： </p> <p> 
     <ul id="ul_A92D90896E5A42C5804AC5CE83E8EB25"> 
      <li id="li_9734EA9C5D9D4F908DE783188C9E5530">在iFrame中無法運作。 這是因為瀏覽器會將iFrame視為協力廠商網域，並防止ID服務設定AMCV Cookie。 </li> 
      <li id="li_3F4BE9048E774902A867D67E5A80674D">無法從父頁面取得訪客ID，因為公司A不使用此服務。 </li> 
     </ul> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>解決方法</b> </p> </td> 
   <td colname="col2"> <p>藉由這些白名單設定來修改 iFrame 中的 ID 服務 <span class="codeph">Visitor.getInstance</span> 函數。在程式碼中指定父網域和子網域。 這些設定可讓iFrame中的ID服務程式碼檢查父頁面上的ID服務程式碼，以取得訪客ID。 </p> <p>如果iFrame中的ID服務程式碼未收到回應父頁面，這些設定會產生本機訪客ID。 </p> </td> 
  </tr> 
 </tbody> 
</table>

## 設定安全與安全性 {#section-2b1ce31fab034e1ca0f6b1c3cc57a6e2}

您可以安全地實作這些設定，因為:

* 在上層網域和 iFrame 網域中實作的 ID 服務必須使用相同的組織 ID。當父代或iFrame中的組織ID不同時，這些白名單設定將無法運作。
* 這些組態只會與程式碼中指定的網域和iFrames通訊。
* iFrame和父頁面之間的通訊會遵循特定格式。 如果父頁面上的ID服務未收到預期格式的請求，此共用程式將失敗。

## 支援的訪客 API 方法 {#section-30c6a9f4dcdc4265a1149260b97cc057}

實作這些白名單設定時，ID 服務支援有限的公用 API 方法集。支援的方法會依上述使用案例情形而有所不同。

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

