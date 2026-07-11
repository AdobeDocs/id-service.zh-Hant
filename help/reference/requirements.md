---
description: 請參閱本節，確定您使用的解決方案、服務及程式碼版本是訪客ID服務要求的正確版本。
keywords: 訪客 ID 服務
title: Adobe訪客ID服務規定
exl-id: ebeac4c7-b36c-4a4e-9378-351fac5baf53
TQID: https://experienceleague.adobe.com/yOoLEIKihVSpDLeZsplTZzg-toOENKlBzsQt2G2YcKk
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
  - id: d3cdead0-685a-4489-9250-4bb709942f66
  - id: df401a2a-327d-468c-a5e4-b7b7ccd071a0
  - id: eddd9b14-83bd-4ff4-9072-54a4a484abb7
source-git-commit: 09ee359440c122702a6ce83708c98af3862c9cc9
workflow-type: tm+mt
source-wordcount: 727
ht-degree: 39%

---

# Adobe訪客ID服務規定 {#requirements-for-the-experience-cloud-id-service}

請參閱本節，確定您使用的解決方案、服務及程式碼版本是訪客ID服務要求的正確版本。

## 需求可確保實作成功並獲得支援 {#section-15e54a9e9ad2443cb9dc950b4a78f1f1}

成功且受支援的實作符合（或超過）程式碼需求，並遵循Adobe說明中的指示。 不受支援的實作會產生非預期的結果，並阻礙客戶服務和我們的工程團隊協助處理或解決訪客ID服務的問題。

### 標準實作

如需您的標準實作，請參閱Adobe Experience Platform資料收集中的[標籤](https://experienceleague.adobe.com/docs/experience-platform/tags/home.html)。

### 非標準實作

對於非標準或手動實作，您必須依照本指南所述的程式來設定訪客ID服務。 如同上述標準實作准則，若程式碼放置和載入錯誤，會建立不受支援的實作。

## CX企業需求：IMS組織ID {#section-a02f537129a64ffbb690d5738d360c26}

若要使用訪客ID服務，貴公司必須啟用CX Enterprise並擁有IMS組織ID。 如果您不確定貴公司的CX Enterprise狀態，且需要尋找您的IMS組織ID，請檢查下列清單。

>[!IMPORTANT]
>
>IMS組織ID區分大小寫，需如實使用。

<table id="table_6C74B676EB094C568D2439FDCC9A7830"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> CX Enterprise狀態 </th> 
   <th colname="col2" class="entry"> 說明 </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <b>已啟用</b> </p> </td> 
   <td colname="col2"> <p>如果貴公司已啟用CX Enterprise，但您沒有您的IMS組織ID，請參閱<a href="https://experienceleague.adobe.com/docs/core-services/interface/manage-users-and-products/organizations.html?lang=zh-Hant" format="https" scope="external">組織ID</a> （向下捲動至<i>尋找組織ID</i>區段）。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>不確定</b> </p> </td> 
   <td colname="col2"> <p> 如果您不清楚公司的CX Enterprise狀態，但同事可使用Adobe ID登入<a href="https://experiencecloud.adobe.com" format="https" scope="external"> marketing.adobe.com</a>，請詢問負責管理Adobe帳戶的人員。 如果可以的話，表示您已啟用，管理員可以檢視您的IMS組織ID。 若要尋找IMS組織ID，請參閱<a href="https://experienceleague.adobe.com/docs/core-services/interface/experience-cloud.html?lang=zh-Hant" format="https" scope="external"> CX Enterprise Administration</a>中的「Administration Page」一節。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>未啟用</b> </p> </td> 
   <td colname="col2"> <p> 如果貴公司未啟用CX Enterprise，請參閱<a href="https://experienceleague.adobe.com/docs/core-services/interface/about-core-services/core-services.html?lang=zh-Hant" format="https" scope="external">核心服務 — 啟用解決方案</a>以開始使用。 </p> </td> 
  </tr> 
 </tbody> 
</table>

## Analytics 需求：地區資料收集 (RDC) {#section-7d04bb013bc84a25bae3b148bc0ca25f}

所有追蹤伺服器均已轉換為 RDC，因此不需要變更 Analytics 追蹤伺服器。 [更多資訊...](https://experienceleague.adobe.com/docs/analytics/technotes/rdc/regional-data-collection.html?lang=zh-Hant)

## 程式碼資料庫和版本需求 {#section-ad7542a4317d430fa79fc6b095beb84d}

下節列出使用訪客ID服務所需的最低程式碼版本。

>[!TIP]
>
>建議您使用最新版程式碼，而非需求所列的最低版本。

**JavaScript**

<table id="table_8E773F76DBCB4797A0C117080CA8707C"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> CX企業解決方案 </th> 
   <th colname="col3" class="entry"> 程式碼程式庫 </th> 
   <th colname="col4" class="entry"> 版本需求 </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <b>訪客ID服務</b> </p> </td> 
   <td colname="col3"> <p> <span class="codeph"> VisitorAPI.js</span> </p> </td> 
   <td colname="col4"> <p>2.0 或更新版本 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1" morerows="2"> <p> <b> <span class="keyword"> Analytics </span> </b> </p> </td> 
   <td colname="col3"> <p> <span class="codeph"> AppMeasurement.js</span> </p> <p>請參閱 <a href="https://experienceleague.adobe.com/docs/analytics/implementation/js/overview.html?lang=zh-Hant" format="https" scope="external">JavaScript 適用的 AppMeasurement</a>。 </p> </td> 
   <td colname="col4"> <p>1.6.4 或更新版本。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col3"> <p> <span class="codeph"> s_code.js</span> </p> </td> 
   <td colname="col4"> <p>H.27 </p> <p> <p>注意： <span class="keyword"> Analytics</span> s_code H.27版不再受訪客ID服務1.6.0版支援。 將您的程式碼升級至最新版AppMeasurement。 </p> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col3"> <p>影片心率 </p> <p>請參閱 <a href="https://experienceleague.adobe.com/docs/media-analytics/using/media-overview.html?lang=zh-Hant" format="https" scope="external">JavaScript 適用的影片心率 2.x</a>。 </p> </td> 
   <td colname="col4"> <p>2.0 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b> <span class="keyword"> Audience Manager </span> </b> </p> </td> 
   <td colname="col3"> <p> <span class="codeph"> dil.js</span> </p> <p> 請參閱<a href="https://experienceleague.adobe.com/docs/audience-manager/user-guide/dil-api/dil-overview.html?lang=zh-Hant" format="https" scope="external">資料整合程式庫</a> (DIL)。 </p> </td> 
   <td colname="col4"> <p>5.0 </p></td> 
  </tr> 
  <tr> 
   <td colname="col1" morerows="1"> <p> <b> <span class="keyword"> Target </span> </b> </p> </td> 
   <td colname="col3"> <p> <span class="codeph"> mbox.js</span> </p> <p>請參閱 <a href="https://experienceleague.adobe.com/en/docs/target-dev/developer/client-side/at-js-implementation/at-js/overview" format="https" scope="external">Mbox 程式碼</a>。 </p> </td> 
   <td colname="col4"> <p>61 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col3"> <p> <span class="codeph"> at.js</span> </p> <p>請參閱 <a href="https://experienceleague.adobe.com/en/docs/target-dev/developer/client-side/at-js-implementation/at-js/how-atjs-works" format="https" scope="external">at.js 實作</a>。 </p> </td> 
   <td colname="col4"> <p>0.9.1 </p> </td> 
  </tr> 
 </tbody> 
</table>

## Android 和 iOS 的 SDK 需求 {#section-73b2446fba8e463888642c7d7dfd94f1}

訪客ID服務至少需要下列SDK版本。

* Android：4.11.0
* iOS：4.11.0

>[!TIP]
>
>建議您使用最新版程式碼，而非需求所列的最低版本。

必須為訪客ID服務啟用您的SDK程式碼。 請在 [Adobe Mobile Services](https://mobilemarketing.adobe.com/) 帳戶中，為每個應用程式啟用並下載最新的 SDK 程式碼。 另請參閱:

* [配置 SDK 訪客 ID 服務選項](https://experienceleague.adobe.com/docs/mobile-services/using/manage-app-settings-ug/configuring-app/t-config-visitor.html?lang=zh-Hant)
* [Android SDK 方法](https://experienceleague.adobe.com/docs/mobile-services/android/experience-cloud-android/c-marketing-cloud.html?lang=zh-Hant)
* [iOS SKD方法](https://experienceleague.adobe.com/docs/mobile-services/ios/exp-cloud-ios/marketing-cloud.html?lang=zh-Hant)

>[!MORELIKETHIS]
>
>* [程式碼程式庫](../library/library.md#concept-ff27497375644a898d47984aefb21c97)
