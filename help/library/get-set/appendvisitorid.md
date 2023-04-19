---
description: 瀏覽器封鎖第三方 Cookie 時，此函數可讓您跨網域共用訪客的 Experience Cloud ID。若要使用此函數，您必須先實作 ID 服務，且擁有來源和目的地的網域。適用於 VisitorAPI.js 1.7.0 版或更新版本。
keywords: ID 服務
title: appendVisitorIDsTo (跨網域追蹤)
exl-id: 3e4f4e2c-e658-4124-bd0e-59c63127bdde
source-git-commit: 70e0ff00be9037b475084a906405180107f2514c
workflow-type: tm+mt
source-wordcount: '337'
ht-degree: 96%

---

# appendVisitorIDsTo (跨網域追蹤){#appendvisitoridsto-cross-domain-tracking}

瀏覽器封鎖第三方 Cookie 時，此函數可讓您跨網域共用訪客的 Experience Cloud ID。若要使用此函數，您必須先實作 ID 服務，且擁有來源和目的地的網域。適用於 VisitorAPI.js 1.7.0 版或更新版本。

內容:

<ul class="simplelist"> 
 <li> <a href="../../library/get-set/appendvisitorid.md#section-7251d88befd440b4b79520e33c5aa44a" format="dita" scope="local"> 在第三方 Cookie 遭到瀏覽器封鎖時跨網域追蹤訪客 </a> </li> 
 <li> <a href="../../library/get-set/appendvisitorid.md#section-62d55f7f986542b0b9238e483d50d7b0" format="dita" scope="local"> 附加訪客 ID 程式碼範例 </a> </li> 
 </a> </li> 
</ul>

<!-- <li> <a href="../../library/get-set/appendvisitorid.md#section-168e313df6054af0a7e27b9fa0d69640" format="dita" scope="local"> Dynamic Tag Management (DTM) and SDK Support -->

## 在第三方 Cookie 遭到瀏覽器封鎖時跨網域追蹤訪客 {#section-7251d88befd440b4b79520e33c5aa44a}

當用戶造訪您的網站，ID 服務會將第一方和第三方 Cookie 寫入瀏覽器 (請參閱 [Cookie 與 Experience Cloud Identity Service](../../introduction/cookies.md))。第一方 Cookie 包含 MID，此為該訪客的唯一 ID。第三方 Cookie 包含 ID 服務用來產生 MID 的其他 ID。當瀏覽器封鎖此第三方 Cookie 時，ID 服務將無法：

* 在該網站訪客瀏覽至其他網域時為其重新產生唯一 ID。
* 在組織所擁有的不同網域間追蹤訪客。

為解決此問題，請實作 ` Visitor.appendVisitorIDsTo( *``*)`。此屬性可讓 ID 服務在多個網域間追蹤網站訪客，即使瀏覽器封鎖第三方 Cookie 亦然。其運作方式如下：

* 訪客瀏覽至您的其他網域時，` Visitor.appendVisitorIDsTo( *`url`*)` 會附加 MID 作為 URL 重新導向 (從原始網域重新導向至目的地網域) 中的查詢參數。
* 目的地網域的 ID 服務程式碼會從 URL 提取 MID，而非向 Adobe 傳送請求索取該訪客的 ID。此要求包含第三方 Cookie ID，而該 ID 在此案件中無法使用。
* 目的地頁面上的 ID 服務程式碼會使用傳入的 MID 追蹤訪客。

如需詳細資訊，請參閱程式碼範例。

## 附加訪客 ID 程式碼範例 {#section-62d55f7f986542b0b9238e483d50d7b0}

下列范常式式碼可協助您開始使用 `appendVisitorIDsTo` 函式：

```js
var adbeDomains = ["marketo.com", "figma.com", "workfront.com"];
var visitor = Visitor.getInstance("9E1005A551ED61CA0A490D45@AdobeOrg", {
  trackingServer: "sstats.adobe.com",
  trackingServerSecure: "sstats.adobe.com",
  marketingCloudServer: "sstats.adobe.com",
  marketingCloudServerSecure: "sstats.adobe.com"
});
adbeDomains.forEach(function(domain) {
  var domainRegex = RegExp(domain);
  if (!domainRegex.test(location.hostname)) {
    hrefSelector = '[href*="' + domain + '"]';
    document.querySelectorAll(hrefSelector).forEach(function(href) {
      href.addEventListener('mousedown', function(event) {
        var destinationURLWithVisitorIDs = visitor.appendVisitorIDsTo(event.currentTarget.href)
        event.currentTarget.href = destinationURLWithVisitorIDs.replace(/MCAID%3D.*%7CMCORGID/, 'MCAID%3D%7CMCORGID');
      });
    });
  }
});
```

<!-- >[!IMPORTANT]
>
>In order for the values passed in the URL via appendVisitorsIDsTo to be picked up, the [ovewriteCrossDomainMCIDAndAID](../function-vars/overwrite-visitor-id.md) variable must be set to true.

The following example can help you get started with ` Visitor.appendVisitorIDsTo( *`url`*)`. When implemented properly, your JavaScript code could look similar to the following example.

```js
//Code on Domain A 
var destinationURL = "www.destination.com"; 
 
//Call the ID service 
var visitor = Visitor.getInstance(...); 
 
//Append visitor IDs to the destination URL 
var destinationURLWithVisitorIDs = visitor.appendVisitorIDsTo(destinationURL); 
     //Result of appendVisitorIDsTo includes destination URL, Experience Cloud ID (MCMID), and Analytics ID (MCAID) 
     "www.destination.com?adobe_mc=MCMID=1234|MCAID=5678"
//Redirect to the destination
``` -->

<!-- ## Dynamic Tag Management (DTM) and SDK Support {#section-168e313df6054af0a7e27b9fa0d69640}

<table id="table_6E7152B4FD2B4C4D8C9477C68204C4FF"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Support for </th> 
   <th colname="col2" class="entry"> See </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <b>DTM</b> </p> </td> 
   <td colname="col2"> <p> <a href="https://helpx.adobe.com/dtm/kb/how-to-set-marketing-cloud-id-service-helper-function-in-adobe-d.html" format="https" scope="external"> Set the appendVisitorIDTo Function in DTM </a> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>SDK</b> </p> </td> 
   <td colname="col2"> 
    <ul id="ul_9D7933FF68EE4C71BAE999B3747F8398"> 
     <li id="li_9036C76AAECC4E639C23020C0C9F2AF8"> <a href="https://experienceleague.adobe.com/docs/mobile-services/android/experience-cloud-android/mc-methods.html" format="https" scope="external"> Android ID Service Methods </a> </li> 
     <li id="li_E49D357905584674BFDFE348345B3849"> <a href="https://experienceleague.adobe.com/docs/mobile-services/ios/exp-cloud-ios/mc-methods.html" format="https" scope="external"> iOS ID Service Methods </a> </li> 
    </ul> </td> 
  </tr> 
 </tbody> 
</table> -->
