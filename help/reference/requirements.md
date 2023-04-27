---
description: 請參閱本節，確定您使用的解決方案、服務及程式碼版本是 Experience Cloud Identity Service 所要求的正確版本。
keywords: ID 服務
title: Experience Cloud Identity Service 的需求
exl-id: ebeac4c7-b36c-4a4e-9378-351fac5baf53
source-git-commit: 159b37e360b586bbada13e34793009e3067de668
workflow-type: tm+mt
source-wordcount: '650'
ht-degree: 100%

---

# Experience Cloud Identity Service 的需求 {#requirements-for-the-experience-cloud-id-service}

請參閱本節，確定您使用的解決方案、服務及程式碼版本是 Experience Cloud Identity Service 所要求的正確版本。

## 需求可確保實作成功並獲得支援 {#section-15e54a9e9ad2443cb9dc950b4a78f1f1}

成功且受支援的實作符合 (或超過) 程式碼需求，並遵循 [!DNL Adobe] 說明中的指示。不受支援的實作會產生無法預料的結果，並阻礙客戶服務和我們的工程團隊協助處理或解決您的 ID 服務相關問題。

### 標準實作

如需標準實作，請參閱 [Experience Platform](https://experienceleague.adobe.com/docs/experience-platform/tags/home.html)。

### 非標準實作

對於非標準或手動實作，您必須依照本指南所述的程序來設定 ID 服務。如同上方的 DTM 指引，如果程式碼放置和載入錯誤，會建立不受支援的實作。

## Experience Cloud 需求：組織 ID {#section-a02f537129a64ffbb690d5738d360c26}

若要使用 ID 服務，貴公司必須啟用 [!DNL Experience Cloud] 並擁有組織 ID。如果您不確定公司的 [!DNL Experience Cloud] 狀態且需要尋找組織 ID，請檢查下列清單。

>[!IMPORTANT]
>
>組織 ID 區分大小寫，且需如實使用。

<table id="table_6C74B676EB094C568D2439FDCC9A7830"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Experience Cloud 狀態 </th> 
   <th colname="col2" class="entry"> 說明 </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <b>已啟用</b> </p> </td> 
   <td colname="col2"> <p>如果貴公司已啟用 <span class="keyword">Experience Cloud</span>，但您沒有公司的組織 ID，請參閱<a href="https://experienceleague.adobe.com/docs/core-services/interface/manage-users-and-products/organizations.html?lang=zh-Hant" format="https" scope="external">組織 ID</a> (向下捲動至「<i>尋找組織 ID</i>」一節)。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>不確定</b> </p> </td> 
   <td colname="col2"> <p> 如果您不清楚公司的 <span class="keyword">Experience Cloud</span> 狀態，但同事可使用 Adobe ID 登入 <a href="https://experiencecloud.adobe.com" format="https" scope="external">marketing.adobe.com</a>，請詢問負責管理 Adobe 帳戶的人員。如果您可登入即表示已啟用，管理員就可檢視您的組織 ID。若要尋找組織 ID，請參閱 <a href="https://experienceleague.adobe.com/docs/core-services/interface/experience-cloud.html?lang=zh-Hant" format="https" scope="external">Experience Cloud 管理</a>的「管理頁面」一節。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>未啟用</b> </p> </td> 
   <td colname="col2"> <p> 如果貴公司未啟用 Experience Cloud，請參閱<a href="https://experienceleague.adobe.com/docs/core-services/interface/about-core-services/core-services.html?lang=zh-Hant" format="https" scope="external">核心服務 - 啟用解決方案</a>以便開始使用。 </p> </td> 
  </tr> 
 </tbody> 
</table>

## Analytics 需求：地區資料收集 (RDC) {#section-7d04bb013bc84a25bae3b148bc0ca25f}

所有追蹤伺服器均已轉換為 RDC，因此不需要變更 Analytics 追蹤伺服器。 [更多資訊...](https://experienceleague.adobe.com/docs/analytics/technotes/rdc/regional-data-collection.html?lang=zh-Hant)

## 程式碼資料庫和版本需求 {#section-ad7542a4317d430fa79fc6b095beb84d}

下節列出使用 [!DNL Experience Cloud] ID 服務所需的最低程式碼版本。

>[!TIP]
>
>建議您使用最新版程式碼，而非需求所列的最低版本。

**JavaScript**

<table id="table_8E773F76DBCB4797A0C117080CA8707C"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Experience Cloud 解決方案 </th> 
   <th colname="col3" class="entry"> 程式碼程式庫 </th> 
   <th colname="col4" class="entry"> 版本需求 </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <b><span class="keyword"></span> Experience Cloud ID 服務</b> </p> </td> 
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
   <td colname="col4"> <p>H.27 </p> <p> <p>注意：<span class="keyword">Analytics</span> s_code H.27 版不再支援 ID 服務 1.6.0 版發行。請將您的程式碼升級至最新版 AppMeasurement。 </p> </p> </td> 
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
   <td colname="col3"> <p> <span class="codeph"> mbox.js</span> </p> <p>請參閱 <a href="https://experienceleague.adobe.com/docs/target/using/implement-target/client-side/mbox-implement/mbox-technical.html?lang=zh-Hant" format="https" scope="external">Mbox 程式碼</a>。 </p> </td> 
   <td colname="col4"> <p>61 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col3"> <p> <span class="codeph"> at.js</span> </p> <p>請參閱 <a href="https://experienceleague.adobe.com/docs/target/using/implement-target/client-side/at-js/how-atjs-works.html?lang=zh-Hant" format="https" scope="external">at.js 實作</a>。 </p> </td> 
   <td colname="col4"> <p>0.9.1 </p> </td> 
  </tr> 
 </tbody> 
</table>

## Android 和 iOS 的 SDK 需求 {#section-73b2446fba8e463888642c7d7dfd94f1}

ID 服務至少需要下列 SDK 版本。

* Android：4.11.0
* iOS：4.11.0

>[!TIP]
>
>建議您使用最新版程式碼，而非需求所列的最低版本。

您必須為 ID 服務啟用 SDK 程式碼。請在 [Adobe Mobile Services](https://mobilemarketing.adobe.com/) 帳戶中，為每個應用程式啟用並下載最新的 SDK 程式碼。另請參閱:

* [配置 SDK 訪客 ID 服務選項](https://experienceleague.adobe.com/docs/mobile-services/using/manage-app-settings-ug/configuring-app/t-config-visitor.html?lang=zh-Hant)
* [Android SDK 方法](https://experienceleague.adobe.com/docs/mobile-services/android/experience-cloud-android/c-marketing-cloud.html?lang=zh-Hant)
* [iOS SKD 方法](https://experienceleague.adobe.com/docs/mobile-services/ios/exp-cloud-ios/marketing-cloud.html?lang=zh-Hant)

>[!MORELIKETHIS]
>
>* [程式碼程式庫](../library/library.md#concept-ff27497375644a898d47984aefb21c97)

