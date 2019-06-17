---
description: Experience Cloud ID 服務取代了舊有的 Analytics 訪客 ID 方法。
keywords: ID 服務
seo-description: Experience Cloud ID 服務取代了舊有的 Analytics 訪客 ID 方法。
seo-title: 設定 Analytics 和 Experience Cloud ID
title: 設定 Analytics 和 Experience Cloud ID
uuid: 421cf597-a03 ca3-8ce8-d0 c80 cbb6 aca
translation-type: tm+mt
source-git-commit: ab9290769cd5fd6d5da7e664bac8ad467cb95166

---


# 設定 Analytics 和 Experience Cloud ID{#setting-analytics-and-experience-cloud-ids}

Experience Cloud ID 服務取代了舊有的 Analytics 訪客 ID 方法。

實作 ID 服務之後，此程式碼會在 AppMeasurement 之前執行。ID 服務會擷取 Experience Cloud 和 Analytics ID，讓這些值在 AppMeasurement 載入時即已備妥。

當 AppMeasurement 載入時，將會從 ID 服務請求 Experience Cloud 和 Analytics ID 值，並透過每個伺服器呼叫將其傳送至資料收集。由於 ID 服務會判斷訪客 ID 並將其傳遞給 AppMeasurement，所以 AppMeasurement JavaScript 檔案前的每個頁面上都必須加入並進行 ID 服務。

## Analytics ID 程序的變更 {#section-79bb86ae63f546419bb1a7ef5e710462}

移轉至 [!DNL Experience Cloud] ID 服務時的主要變更，是現在使用 JavaScript 設定 ID Cookie，而不是使用從資料收集網站伺服器傳回的 HTTP 標題。為了了解此項變更，以下章節說明如何使用這兩種方法來設定 Cookie。

**HTTP 標題**

來自網站伺服器的 HTTP 回應會在瀏覽器中設定 Cookie。這是 `s_vi` Cookie設定的方式。`s_vi` Cookie會識別Analytics訪客。Cookie 設定後，便會隨所有後續 HTTP 請求傳送給該伺服器。

當請求傳送至 Adobe 資料收集伺服器時，會檢查標題中是否有 `s_vi` Cookie。如果請求中有此 Cookie，便會用來識別訪客。如果請求中沒有 Cookie，則伺服器會產生獨特 [!DNL Experience Cloud] ID、在 HTTP 回應標題中將其設定為 Cookie，並隨請求將其傳回。後續造訪網站時，系統會將 Cookie 儲存在瀏覽器中，並傳回資料收集伺服器。因此，訪客再次造訪時即可識別出訪客。

不過，有些瀏覽器不接受第三方 Cookie，例如 Apple Safari。也有 Cookie 是在目前網站，外的網域瀏覽器中設定的。此外，如果訪客之前未造訪過第三方網域，則 Safari 會封鎖該網域的 Cookie。例如，如果您位於 `mysite.com` 而您的資料收集伺服器是 `mysite.omtrdc.net`，則瀏覽器可能會拒絕從 `mysite.omtrdc.net` HTTP 標題中傳回的 Cookie。

為了避免此情況，許多客戶已針對其資料收集伺服器實作 CNAME 記錄。這會是有效的[第一方 Cookie 實作](https://marketing.adobe.com/resources/help/en_US/whitepapers/first_party_cookies/)策略。如果已設定 CNAME 記錄將客戶網域的主機名稱對應至資料收集伺服器 (例如，將 `metrics.mysite.com` 對應至 `mysite.omtrdc.net`)，因為資料收集網域現在符合網站的網域，所以可以儲存 [!DNL Experience Cloud] ID Cookie。如此便增加了儲存 ID 服務 Cookie 的可能性。不過，這確實會帶來一些額外工作，因為您需要設定 CNAME 記錄，並為資料收集伺服器維護 SSL 憑證。

**JavaScript**

JavaScript 可讀取和寫入第一方網域中設定的 Cookie (目前網站的網域)。[!DNL Experience Cloud] ID 服務會使用此方法來設定包含所有訪客 ID 的 `AMCV_###@AdobeOrg` Cookie，使追蹤伺服器的網域不再需要符合網站的網域，即可儲存訪客 ID Cookie。通常我們會使用此方法來設定 ID 服務 Cookie，因為這樣可以消除 CNAME 記錄和 SSL 憑證的額外負荷。

不過，在少數情況下，於 HTTP 標題中設定 Cookie 有利於跨網域追蹤，這在[資料收集 CNAME 和跨網域追蹤](../../mcvid-reference/mcvid-analytics-reference/mcvid-cname.md#concept-4df91f8a30ad4ec7a01eb943d579cc9d)中有相關說明。

## 自訂 Analytics ID {#section-b6a7bd19e9ff432390010062450808f6}

在 Analytics 中，使用 `s.visitorID` 來設定客戶 ID 是辨識使用者的方法。不過使用 ID 服務匯出或匯入的 Analytics 資料整合，在訪客的識別方式為 `s.visitorID` 時無法正常運作。

這種狀況包括但不限於共用受眾、Analytics for Target (A4T) 和客戶屬性。對於這類整合內容，設定自訂 Analytics ID 的方法便不受支援。

## Analytics 訪客 ID 順序 {#section-de1dc9fc9b6d4388995b70e35b8bcddf}

在您部署訪客 ID 服務後，在 Analytics 中有五種方式可用來識別訪客 (依優先順序列於下表中): 

<table id="table_D267D36451F643D1BB68AF6FEAA6AD1A"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> 使用順序 </th> 
   <th colname="col2" class="entry"> 查詢參數 (收集方法) </th> 
   <th colname="col3" class="entry"> 存在時機 </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <img id="image_9F3E58898A1B4F40BBDEF5ADE362E55C" src="assets/step1_icon.png" /> </p> </td> 
   <td colname="col2"> <p> <a href="https://marketing.adobe.com/resources/help/en_US/sc/implement/?f=visid_custom" format="http" scope="external"> vid (s.visitorID)</a> </p> </td> 
   <td colname="col3"> <p>設定 s.visitorID 時 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <img id="image_77A06981672745B6AEA8BB4D55911CCA" src="assets/step2_icon.png" /> </p> </td> 
   <td colname="col2"> <p> <a href="https://marketing.adobe.com/resources/help/en_US/sc/implement/?f=visid_analytics" format="http" scope="external"> aid (s_vi Cookie)</a> </p> </td> 
   <td colname="col3"> <p>訪客在您部署 <span class="keyword"> Experience Cloud</span> ID服務之前已有s_ vi Cookie，或者您已設定 <a href="../../mcvid-reference/mcvid-analytics-reference/mcvid-grace-period.md" format="dita" scope="local"> 寬限期</a> 。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <img id="image_0A950B1A6B004387AFEE8EED882739CB" src="assets/step3_icon.png" /> </p> </td> 
   <td colname="col2"> <p>mid (Experience Cloud 訪客 ID 服務所設定的 AMCV_ Cookie) </p> </td> 
   <td colname="col3"> <p>訪客的瀏覽器接受第一方 Cookie </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <img id="image_6F0ED8FE3EF846CA8E6ECCC3C0070D85" src="assets/step4_icon.png" /> </p> </td> 
   <td colname="col2"> <p> <a href="https://marketing.adobe.com/resources/help/en_US/sc/implement/?f=visid_fallback" format="http" scope="external"> fid (H.25.3 或更新版本的後援 Cookie，或 JavaScript 適用的 AppMeasurement)</a> </p> </td> 
   <td colname="col3"> <p>瀏覽器不接受第三方 Cookie 且 Analytics 追蹤伺服器已設定為第三方追蹤伺服器。 </p> <p> <p>注意: 如果您已在網站上實施 ID 服務，則舊版識別碼 <span class="codeph">fid</span> 並未使用。在這種情況下，不需要 <span class="codeph"> fid</span> ，因為第一方的 <a href="../../mcvid-introduction/mcvid-cookies.md" format="dita" scope="local"> AMCV Cookie會</a> 使它失效。保留它是為了支援舊版程式碼且供歷史記錄之用。 </p> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <img id="image_23D8C0EB69EC4084BC237B5B98C036F4" src="assets/step5_icon.png" /> </p> </td> 
   <td colname="col2"> <p> <a href="https://marketing.adobe.com/resources/help/en_US/sc/implement/?f=visid_fallback" format="http" scope="external"> IP 位址、使用者代理、閘道 IP 位址</a> </p> </td> 
   <td colname="col3"> <p>訪客的瀏覽器不接受 Cookie。 </p> </td> 
  </tr> 
 </tbody> 
</table>

在許多情況下，您可能會在一個呼叫中看見 2 或 3 個不同的 ID，但 Analytics 將會使用清單中第一個出現的 ID 做為正式的 [!DNL Experience Cloud] ID。例如，如果您設定自訂訪客 ID (內含於 &quot;vid&quot; 查詢參數中)，則在同一個點擊可能存在其他 ID 時，將優先使用該自訂訪客 ID。

>[!MORE_贊_ this]
>
>* [Analytics ID 的作業順序](../../mcvid-reference/mcvid-analytics-reference/mcvid-analytics-order-of-operations.md#concept-b92935b4fff545adb4773f3728bc15ef)

