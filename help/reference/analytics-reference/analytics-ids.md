---
description: Experience Cloud Identity 服務會取代舊有的 Analytics 訪客 ID 方法。
keywords: ID Service
seo-description: Experience Cloud Identity 服務會取代舊有的 Analytics 訪客 ID 方法。
seo-title: 設定 Analytics 和 Experience Cloud ID
title: 設定 Analytics 和 Experience Cloud ID
uuid: 421cf597-a3e0-4ca3-8ce8-d0c80cbb6aca
translation-type: tm+mt
source-git-commit: d2bc0e7fedc4e48d51f5dad158f9f8bfcb0cb4f3

---


# 設定 Analytics 和 Experience Cloud ID{#setting-analytics-and-experience-cloud-ids}

Experience Cloud Identity 服務會取代舊有的 Analytics 訪客 ID 方法。

實作ID服務後，此程式碼會在AppMeasurement之前執行。 ID服務會擷取Experience Cloud和Analytics ID，讓這些值在AppMeasurement載入時就緒。

當AppMeasurement載入時，會從ID服務要求Experience Cloud和Analytics ID值，並透過每個伺服器呼叫傳送至資料收集。 由於ID服務會判斷訪客ID，並僅將其傳遞至AppMeasurement，因此必須在AppMeasurement JavaScript檔案前的每個頁面上加入並實作ID服務。

## Analytics ID程式的變更 {#section-79bb86ae63f546419bb1a7ef5e710462}

移轉至 [!DNL Experience Cloud] ID 服務時的主要變更，是現在使用 JavaScript 設定 ID Cookie，而不是使用從資料收集網站伺服器傳回的 HTTP 標題。為了瞭解這項變更，以下章節將說明如何使用這兩種方法來設定Cookie。

**HTTP標題**

來自網頁伺服器的HTTP回應會在瀏覽器中設定Cookie。 這是 `s_vi` Cookie 設定的方法。`s_vi` Cookie 可識別 Analytics 訪客。Cookie 設定後，便會隨所有後續 HTTP 請求傳送給該伺服器。

當請求傳送至 Adobe 資料收集伺服器時，會檢查標題中是否有 `s_vi` Cookie。如果請求中有此 Cookie，便會用來識別訪客。如果請求中沒有 Cookie，則伺服器會產生獨特 [!DNL Experience Cloud] ID、在 HTTP 回應標題中將其設定為 Cookie，並隨請求將其傳回。Cookie會儲存在瀏覽器中，並在後續造訪網站時傳回至資料收集伺服器。 這可讓訪客在瀏覽間識別。

不過，有些瀏覽器（例如Apple Safari）不接受第三方Cookie。 這些是在瀏覽器中，從目前網站以外的網域設定的Cookie。 此外，如果訪客之前未造訪過該網域，Safari會封鎖第三方網域上的Cookie。 例如，如果您位於 `mysite.com` 而您的資料收集伺服器是 `mysite.omtrdc.net`，則瀏覽器可能會拒絕從 `mysite.omtrdc.net` HTTP 標題中傳回的 Cookie。

為了避免此情況，許多客戶已針對其資料收集伺服器實作 CNAME 記錄。This can be an effective part of a [first-party cookie implementation](https://docs.adobe.com/content/help/zh-Hant/core-services/interface/ec-cookies/cookies-first-party.html) strategy. 如果已設定 CNAME 記錄將客戶網域的主機名稱對應至資料收集伺服器 (例如，將 `metrics.mysite.com` 對應至 `mysite.omtrdc.net`)，因為資料收集網域現在符合網站的網域，所以可以儲存 [!DNL Experience Cloud] ID Cookie。這會增加儲存ID服務Cookie的可能性。 不過，這確實會帶來一些額外負荷，因為您需要設定CNAME記錄並維護資料收集伺服器的SSL憑證。

**JavaScript**

JavaScript可讀取和寫入第一方網域（目前網站的網域）中設定的Cookie。 [!DNL Experience Cloud] ID 服務會使用此方法來設定包含所有訪客 ID 的 `AMCV_###@AdobeOrg` Cookie，使追蹤伺服器的網域不再需要符合網站的網域，即可儲存訪客 ID Cookie。在大多數情況下，這是設定ID服務Cookie的偏好方式，因為它可免除CNAME記錄和SSL憑證的負擔。

不過，在某些情況下，在HTTP標題中設定Cookie有利於跨網域追蹤，這在「資料收集CNAME」和「跨網域追蹤」中有所說明 [](../../reference/analytics-reference/cname.md#concept-4df91f8a30ad4ec7a01eb943d579cc9d)。

## 自訂分析ID {#section-b6a7bd19e9ff432390010062450808f6}

在 Analytics 中，使用 `s.visitorID` 來設定客戶 ID 是辨識使用者的方法。不過使用 ID 服務匯出或匯入的 Analytics 資料整合，在訪客的識別方式為 `s.visitorID` 時無法正常運作。

這種狀況包括但不限於共用受眾、Analytics for Target (A4T) 和客戶屬性。對於這類整合內容，設定自訂 Analytics ID 的方法便不受支援。

## Analytics 訪客 ID 順序 {#section-de1dc9fc9b6d4388995b70e35b8bcddf}

在您部署訪客 ID 服務後，在 Analytics 中有五種方式可用來識別訪客 (依優先順序列於下表中)：

<table id="table_D267D36451F643D1BB68AF6FEAA6AD1A"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> 使用的訂單 </th> 
   <th colname="col2" class="entry"> 查詢參數（收集方法） </th> 
   <th colname="col3" class="entry"> 在 </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <img id="image_9F3E58898A1B4F40BBDEF5ADE362E55C" src="assets/step1_icon.png" /> </p> </td> 
   <td colname="col2"> <p> <a href="https://docs.adobe.com/content/help/en/analytics/implementation/vars/config-vars/visitorid.html" format="http" scope="external"> vid (s.visitorID)</a> </p> </td> 
   <td colname="col3"> <p>設定 s.visitorID 時 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <img id="image_77A06981672745B6AEA8BB4D55911CCA" src="assets/step2_icon.png" /> </p> </td> 
   <td colname="col2"> <p> <a href="https://docs.adobe.com/content/help/en/core-services/interface/ec-cookies/cookies-analytics.html" format="http" scope="external"> aid (s_vi Cookie)</a> </p> </td> 
   <td colname="col3"> <p>在您部署 <span class="keyword">Experience Cloud</span> ID 服務之前訪客已有 s_vi Cookie，或是您已設定<a href="../../reference/analytics-reference/grace-period.md" format="dita" scope="local">寬限期</a>。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <img id="image_0A950B1A6B004387AFEE8EED882739CB" src="assets/step3_icon.png" /> </p> </td> 
   <td colname="col2"> <p>mid（由Experience Cloud訪客ID服務設定的AMCV_ Cookie） </p> </td> 
   <td colname="col3"> <p>訪客的瀏覽器接受第一方 Cookie </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <img id="image_6F0ED8FE3EF846CA8E6ECCC3C0070D85" src="assets/step4_icon.png" /> </p> </td> 
   <td colname="col2"> <p> <a href="https://docs.adobe.com/content/help/en/id-service/using/reference/analytics-reference/analytics-ids.html" format="http" scope="external"> fid (H.25.3 或更新版本的後援 Cookie，或 JavaScript 適用的 AppMeasurement)</a> </p> </td> 
   <td colname="col3"> <p>瀏覽器不接受第三方 Cookie 且 Analytics 追蹤伺服器已設定為第三方追蹤伺服器。 </p> <p> <p>注意：如果您已在網站上實作 ID 服務，則舊版識別碼 <span class="codeph">fid</span> 並未使用。在此情況下就不需要 <span class="codeph">fid</span>，因為第一方 <a href="../../introduction/cookies.md" format="dita" scope="local"> AMCV Cookie</a> 已將其淘汰。保留它是為了支援舊版程式碼且供歷史記錄之用。 </p> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <img id="image_23D8C0EB69EC4084BC237B5B98C036F4" src="assets/step5_icon.png" /> </p> </td> 
   <td colname="col2"> <p> <a href="https://docs.adobe.com/content/help/zh-Hant/analytics/technotes/visitor-identification.html" format="http" scope="external"> IP 位址、使用者代理、閘道 IP 位址</a> </p> </td> 
   <td colname="col3"> <p>訪客的瀏覽器不接受 Cookie。 </p> </td> 
  </tr> 
 </tbody> 
</table>

在許多情況下，您可能會在一個呼叫中看見 2 或 3 個不同的 ID，但 Analytics 將會使用清單中第一個出現的 ID 做為正式的 [!DNL Experience Cloud] ID。例如，如果您設定自訂訪客 ID (內含於 &quot;vid&quot; 查詢參數中)，則在同一個點擊可能存在其他 ID 時，將優先使用該自訂訪客 ID。

>[!MORELIKETHIS]
>
>* [Analytics ID 的作業順序](../../reference/analytics-reference/analytics-order-of-operations.md#concept-b92935b4fff545adb4773f3728bc15ef)

