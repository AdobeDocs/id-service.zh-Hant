---
description: 瀏覽器封鎖第三方 Cookie 時，此函數可讓您跨網域共用訪客的 ECID。 若要使用此函式，您必須先實作訪客ID服務，且擁有來源和目的地網域。 適用於 VisitorAPI.js 1.7.0 版或更新版本。
keywords: 訪客 ID 服務
title: appendVisitorIDsTo (跨網域追蹤)
exl-id: 3e4f4e2c-e658-4124-bd0e-59c63127bdde
TQID: https://experienceleague.adobe.com/F4rWmYj6NidX861-qU8KI9RRbdwNdzP0x4CZUxPZfYw
product_v2:
  - id: e1971122-7081-4556-9222-8a31bd71800c
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: f8a45b24-4be7-4f1b-909b-60d06b483a20
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
  - id: c2be0313-b3ae-45e0-b454-d20bf54b23f2
source-git-commit: 09ee359440c122702a6ce83708c98af3862c9cc9
workflow-type: tm+mt
source-wordcount: 432
ht-degree: 50%

---

# appendVisitorIDsTo (跨網域追蹤){#appendvisitoridsto-cross-domain-tracking}

>[!TIP]
>
>如果ECID最初遭到拒絕（或先前遭拒），跨網域追蹤將無法如預期運作。 這不會檢查透過URL傳遞的或之前存在於Cookie中的現有ID，考慮這些ID是同意設為「NO」時的ID。

瀏覽器封鎖第三方 Cookie 時，此函數可讓您跨網域共用訪客的 ECID。 若要使用此函式，您必須先實作訪客ID服務，且擁有來源和目的地網域。 可用於`VisitorAPI.js` 1.7.0版或更新版本。

內容:

<ul class="simplelist"> 
 <li> <a href="../../library/get-set/appendvisitorid.md#section-7251d88befd440b4b79520e33c5aa44a" format="dita" scope="local"> 在第三方 Cookie 遭到瀏覽器封鎖時跨網域追蹤訪客 </a> </li> 
 <li> <a href="../../library/get-set/appendvisitorid.md#section-62d55f7f986542b0b9238e483d50d7b0" format="dita" scope="local"> 附加訪客 ID 程式碼範例 </a> </li> 
 </a> </li> 
</ul>

## 在第三方 Cookie 遭到瀏覽器封鎖時跨網域追蹤訪客 {#section-7251d88befd440b4b79520e33c5aa44a}

訪客ID服務會在有人造訪您的網站時，將第一方和第三方Cookie寫入瀏覽器（請參閱[Cookie和訪客ID服務](../../introduction/cookies.md) ）。 第一方 Cookie 包含 MID，此為該訪客的唯一 ID。 第三方Cookie包含訪客ID服務用來產生MID的其他ID。 當瀏覽器封鎖此第三方Cookie時，訪客ID服務無法：

* 在該網站訪客瀏覽至其他網域時為其重新產生唯一 ID。
* 在組織所擁有的不同網域間追蹤訪客。

為解決此問題，請實作 `Visitor.appendVisitorIDsTo( *`&#x200B;`*)`。 此屬性可讓訪客ID服務在多個網域間追蹤網站訪客，即使瀏覽器封鎖第三方Cookie亦然。 其運作方式如下：

* 訪客瀏覽至您的其他網域時，`Visitor.appendVisitorIDsTo( *`url`*)` 會附加 MID 作為 URL 重新導向 (從原始網域重新導向至目的地網域) 中的查詢參數。
* 目的地網域的訪客ID服務程式碼會從URL提取MID，而非傳送要求向Adobe索取該訪客的ID。 此要求包含第三方 Cookie ID，而該 ID 在此案件中無法使用。
* 目的地頁面上的訪客ID服務程式碼會使用傳入的MID追蹤訪客。

如需詳細資訊，請參閱程式碼範例。

## 附加訪客 ID 程式碼範例 {#section-62d55f7f986542b0b9238e483d50d7b0}

以下範例程式碼可幫助您開始使用 `appendVisitorIDsTo` 函數：

>[!TIP]
>
>此程式碼可以放在自訂程式碼編輯器 (Adobe Analytics 擴充功能的一部分)，或放在 [AppMeasurement.js](https://experienceleague.adobe.com/docs/analytics/implementation/js/overview.html?lang=zh-Hant) 的上方。

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

<!-- 
>[!IMPORTANT]
>
>In order for the values passed in the URL via appendVisitorsIDsTo to be picked up, the [ovewriteCrossDomainMCIDAndAID](../function-vars/overwrite-visitor-id.md) variable must be set to true.

The following example can help you get started with `Visitor.appendVisitorIDsTo( *`url`*)`. When implemented properly, your JavaScript code could look similar to the following example.

```js
//Code on Domain A 
var destinationURL = "www.destination.com"; 
 
//Call the Visitor ID Service 
var visitor = Visitor.getInstance(...); 
 
//Append visitor IDs to the destination URL 
var destinationURLWithVisitorIDs = visitor.appendVisitorIDsTo(destinationURL); 
     //Result of appendVisitorIDsTo includes destination URL, ECID (MCMID), and Analytics ID (MCAID) 
     "www.destination.com?adobe_mc=MCMID=1234|MCAID=5678"
//Redirect to the destination
``` 
-->

<!--
## SDK Support {#section-168e313df6054af0a7e27b9fa0d69640}

<table id="table_6E7152B4FD2B4C4D8C9477C68204C4FF"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Support for </th> 
   <th colname="col2" class="entry"> See </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <b>SDK</b> </p> </td> 
   <td colname="col2"> 
    <ul id="ul_9D7933FF68EE4C71BAE999B3747F8398"> 
     <li id="li_9036C76AAECC4E639C23020C0C9F2AF8"> <a href="https://experienceleague.adobe.com/docs/mobile-services/android/experience-cloud-android/mc-methods.html?lang=zh-Hant" format="https" scope="external"> Android Visitor ID Service Methods </a> </li> 
     <li id="li_E49D357905584674BFDFE348345B3849"> <a href="https://experienceleague.adobe.com/docs/mobile-services/ios/exp-cloud-ios/mc-methods.html?lang=zh-Hant" format="https" scope="external"> iOS Visitor ID Service Methods </a> </li> 
    </ul> </td> 
  </tr> 
 </tbody> 
</table> 
-->

