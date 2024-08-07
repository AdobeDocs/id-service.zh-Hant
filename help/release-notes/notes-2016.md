---
description: 2016 年 Experience Cloud Identity Service 的功能發佈、更新或變更。
keywords: ID 服務
title: 2016 年版本注意事項
feature-set: Experience Cloud Services
feature: TK421
exl-id: f96b9869-6282-4090-b392-797608e25a51
source-git-commit: d027f7fca8cf62d6b5d80ec3c37049ddd1afdd70
workflow-type: tm+mt
source-wordcount: '1175'
ht-degree: 100%

---

# 2016 年版本注意事項 {#release-notes}

2016 年 Experience Cloud Identity Service 的功能發佈、更新或變更。

這些變更也包含在 [Experience Cloud 版本注意事項](https://experienceleague.adobe.com/docs/release-notes/experience-cloud/current.html?lang=zh-Hant)中。

## 1.10 版 {#section-7d719b3213344a46858835042e0214ed}

2016 年 11 月

>[!IMPORTANT]
>
>* 1.10 版需使用 [!UICONTROL AppMeasurement] 1.8.0 版。
>* 使用 Experience Cloud Identity Service Library 2.0.0+ 時，Adobe Media Optimizer 會依預設開始執行 ID 同步作業。請參閱[了解 ID 同步和匹配率](/help/introduction/match-rates.md)。

**修正和改良**

* 新增如何在伺服器端環境中實作 ID 服務的指示。
* 新增 `Visitor.overwriteCrossDomainMCIDAndAID`，此布林值函數可讓您覆寫在其他網域上擁有的 Experience Cloud 和 Analytics ID。請參閱[覆寫訪客 ID](../library/function-vars/overwrite-visitor-id.md#reference-9db13d637ce44fb6a8d519de5743ccde)。

* 新增 `TS = UTC` 時間戳記 作為 `visitor.appendVisitorIDsTo` 函數的屬性。ID 服務會使用時間戳記，判斷是否應根據 5 分鐘的時效間隔在重新導向 URL 中使用 ID。請參閱[附加訪客 ID 函數](../library/get-set/appendvisitorid.md#reference-ff167ef19e37433fb08ac2b5a86229ce)。

* 新增 `Visitor.getLocationHint,`，此新函數可傳回地區 ID。請參閱[取得地區 ID (位置提示)](../library/get-set/getlocationhint.md#reference-a761030ff06c4439946bb56febf42d4c)。

* 新增 `idSyncByURL` 和 `idSyncByDataSource` 這兩項功能，可讓您在 Destination Publishing iFrame 中手動實作 ID 同步。請參閱[依 URL 或資料來源執行 ID 同步作業](../library/get-set/idsync.md#reference-b01b88c083434cf8abbeabd3c6956c48)。

* 修正若出現 `disableThirdPartyCalls:true` 時封鎖 AppMeasurement 追蹤呼叫的錯誤。
* 修正會讓 ID 服務無法將 Experience Cloud ID (MID) 傳遞至其他網域的錯誤。

## 1.9.0 版 {#section-04e1b4d4b10d40468f2116b8119998e7}

2016 年 10 月

**修正和改良**

* 修正了將 Audience Manager 唯一用戶 ID (AAMUUID) 做為 Experience Cloud ID 傳至 ID 服務的錯誤。
* 如果 AMCV Cookie 的存留時間 (TTL) 已過期，只要 Cookie 包含 Experience Cloud ID，ID 服務仍會將該資訊傳回至伺服器。在此呼叫後，ID 服務會進行非同步呼叫以更新 Cookie。這有助於改善效能，因為 ID 服務不需要等待伺服器回應。它可使用現有的 AMCV Cookie 值，然後請求更新。
* ID 服務會直接在頁面上自動同步 Experience Cloud ID (MID) 與 Adobe Media Optimizer 和其他內部 Adobe 網域。已針對所有現有帳戶與新帳戶啟用自動同步。這有助於改善 Media Optimizer 的匹配率。適用於 VisitorAPI.js 1.8 或更新版本。另請參閱[了解 ID 同步和比對率](../introduction/match-rates.md#concept-e55cf228b90c457fbee8c3cb06b195ab)。

**新文件及修訂的文件**

**新增：**[從 AMCV Cookie 取得地區與用戶 ID](../reference/regions.md#concept-15b2c8c894b846a48f1f61a353cfdf4e)

## 1.8.0 版 {#section-69f2eb5b246b4c7aafe116b7a2a5448a}

2016 年 9 月

**修正和改良**

新增 `disableThirdPartyCalls` 作為選用布林值標幟，您可以在 `Visitor.getInstance` 函數中加以設定。若 `disableThirdPartyCalls= true`，ID 服務將不會呼叫其他網域。根據預設，`disableThirdPartyCalls= false`。請參閱 [disableThirdPartyCalls](../library/function-vars/disablethirdpartycalls.md#reference-fba90b095e9746daad46e3abb790d18b)。

## 1.7.0 版 {#section-f7d59104de6644fca3691480383d4644}

2016 年 8 月

**修正和改良**

* 新增 `idSyncAttachIframeOnWindowLoad` 作為選用布林值標幟，您可以在 `Visitor.getInstance` 函數中加以設定。當 `idSyncAttachIframeOnWindowLoad= true`，ID 服務會在視窗負載上載入 ID 同步 iFrame。根據預設，ID 服務會儘快載入 iFrame。此標幟會「取代」**&#x200B;已廢止的 `idSyncAttachIframeASAP`。請參閱 [Visitor.getInstance 函數變數](../library/function-vars/function-vars.md)。

* 新增相關功能，支援針對網頁轉換數，在網域、原生應用程式和混合式應用程式中追蹤 [!DNL Experience Cloud] ID。請參閱[附加訪客 ID 輔助函數](../library/get-set/appendvisitorid.md#reference-ff167ef19e37433fb08ac2b5a86229ce)。

* 新增函數至 visitorAPI.js 程式碼，判斷 ID 服務是在用戶端或伺服器端產生訪客 [!DNL Experience Cloud] ID，或 ID 呼叫是否已逾時。請參閱[逾時追蹤函數](../library/get-set/timeout-functions.md#reference-912bae0f116540df8c5dc1c008656c23)和[追蹤用戶端訪客 ID 產生](../library/get-set/client-side-id.md#reference-8244dc6d832c4bbaaa97528096bcc2a6)。

**新文件及修訂的文件**

修訂：[Experience Cloud Identity Service 的需求](../reference/requirements.md)

**已知問題**

在同一頁上使用 [!DNL Audience Manager] DIL 程式碼和 visitorAPI.js 程式碼的客戶，應將 DIL 變數設為 `secureDataCollection= false`。請參閱 [secureDataCollection](https://experienceleague.adobe.com/docs/audience-manager/user-guide/dil-api/dil-overview.html?lang=zh-Hant)。

## 1.6.0 版 {#section-3faaa14bf3934c6a99b8f79ee06fc0d2}

2016 年 7 月

>[!IMPORTANT]
>
>[!DNL Experience Cloud] ID 服務 1.6.0 版&#x200B;*需要* JavaScript 適用的 AppMeasurement 1.6.2 版。如果您升級至 ID 服務 1.6.0 版，請務必確定所用的 AppMeasurement 程式碼版本正確無誤。

<table id="table_5472AAFA0DD2495DB8D92DEBE44A07A9"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> 功能 </th> 
   <th colname="col2" class="entry"> 說明 </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p>跨原始資源共用 (CORS) </p> </td> 
   <td colname="col2"> <p>CORS 可讓瀏覽器從現行網域以外的網域請求資源。Experience Cloud Identity Service 支援 CORS 標準，以允許用戶端的跨原始資源要求。此 ID 服務在不支援 CORS 的瀏覽器上會回復為 JSONP 請求。 </p> <p>請參閱: </p> 
    <ul id="ul_15386385108F4E07824041DD6F2DC11E"> 
     <li id="li_DB8D5AA4A7004DE4AE9CBC31A389F5BD"> <a href="../reference/cors.md#concept-6c280446990d46d88ba9da15d2dcc758" format="dita" scope="local"> Experience Cloud Identity Service 的 CORS 支援 </a> </li> 
    </ul> </td> 
  </tr> 
 </tbody> 
</table>

**修正和改良**

* 將 `d_fieldgroup` 參數新增至 `dpm.demdex.net` 的 ID 同步呼叫。這個新參數可用於內部疑難排解和偵錯。

* 在 ID 服務 iFrame 中新增了標題屬性。iFrame 標題可協助螢幕助讀程式為需要協助的用戶提供頁面資訊，以便他們操作線上內容。iFrame 標題屬性設為 `Adobe ID Syncing iFrame`。
* 新增 `idSyncAttachIframeASAP: true` 作為選用旗標，您可以在 `Visitor.getInstance` 函數中加以設定。若為 `true`，ID 服務便會儘快載入 ID 同步 iFrame。其目的是要改善 ID 同步匹配率。依預設，ID 服務會在視窗載入時載入 iFrame。請參閱 [Visitor.getInstance 函數變數](../library/function-vars/function-vars.md)。

* 修正回呼函數的錯誤，此錯誤使 AppMeasurement 陷入無限迴圈中。
* 將預設 `loadTimeout` 時間間隔從 500 毫秒變更為 30,000 毫秒。請參閱 [Visitor.getInstance 函數變數](../library/function-vars/function-vars.md)。

**新文件及修訂的文件**

**新增**

* [實作適用於 Analytics 的 Experience Cloud Identity Service](../implementation-guides/setup-analytics.md#concept-9ebbea85cb844a15b557be572cd142fd)
* [實作適用於 Analytics、Audience Manager 和 Target 的 Experience Cloud Identity Service](../implementation-guides/setup-aam-analytics-target.md#concept-e7e2dc0d0bbe481db93328b5604b4673)

**修訂**

* [Experience Cloud Identity Service 的需求](../reference/requirements.md)
* [測試及驗證 Experience Cloud Identity Service](../implementation-guides/test-verify.md)

## 1.5.7 版 {#section-735b4989a5744a42aeb2d97602dbda62}

2016 年 6 月

<table id="table_5D604D0820C84EC996ACB99126C8A3DF"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> 功能 </th> 
   <th colname="col2" class="entry"> 說明 </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p>變更 <span class="codeph">iframe.sandbox</span> 屬性 </p> </td> 
   <td colname="col2"> <p>iFrame 現已設定為 <span class="codeph">iframe.sandbox='allow-scripts allow-same-origin';</span>。 </p> <p>僅允許這兩個 Token 協助改善安全性，並提供 ID 服務需要用來同步 ID 的基本功能。 </p> <p>Internet Explorer 9 或更早版本均不支援 sandbox 屬性。如需詳細資訊，請參閱 <a href="https://developer.mozilla.org/zh-TW/docs/Web/HTML/Element/iframe" format="https" scope="external">iFrame 文件</a>中的「屬性」一節。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>對 Experience Cloud ID (MID) 進行編碼 </p> </td> 
   <td colname="col2"> <p>ID 服務會對伺服器傳回的 MID 值或 <span class="codeph">visitor.setMarketingCloudVisitorID()</span> 函式設定的 MID 值進行編碼。如需有關 MID 的詳細資訊，請參閱 <a href="../introduction/cookies.md" format="dita" scope="local">Cookie 與 Experience Cloud ID</a>。 </p> </td> 
  </tr> 
 </tbody> 
</table>

**修正**

若無舊有的 Analytics 訪客 ID，訪客 API 即不會再藉由 Audience Manager 強制執行額外的重新同步呼叫。

## 1.5.x 版 {#section-a62ae48275324058b57edf66ee5a579f}

2016 年 5 月

**文件更新**

* [Android 和 iOS 的 SDK 需求](../reference/requirements.md#section-73b2446fba8e463888642c7d7dfd94f1)
* [Data Workbench 與 Experience Cloud Identity Service](../reference/dwb.md#task-72df50a051944a47b01b0c0bc3d1e1d8)
* [測試及驗證 Experience Cloud Identity Service](../implementation-guides/test-verify.md)

## 1.5.x 版 {#section-0cfeef085cff4cbc8dff6cbc6fc32920}

2016 年 4 月

**文件更新**

[實作適用於 Target 的 Experience Cloud Identity Service](../implementation-guides/setup-target.md#concept-9b5a802132574e1181927ddd00e5c5af)

## 1.5.4 版 {#section-1a44ba147fb3440ea7dec551faee3528}

2016 年 3 月

<table id="table_F4ED1F88709E4D3BA69C747879A4E18F"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> 功能 </th> 
   <th colname="col2" class="entry"> 說明 </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p>選擇退出支援 </p> </td> 
   <td colname="col2"> <p><span class="keyword">Experience Cloud</span> ID 服務支援訪客選擇退出的要求。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> 變更 ID 同步時間間隔 </p> </td> 
   <td colname="col2"> <p><span class="keyword"></span>Experience Cloud ID 服務現在會在每次呼叫資料收集伺服器時進行 ID 同步呼叫。先前的 ID 服務只會在首次呼叫以取得 <span class="keyword">Experience Cloud</span> ID 時提出 1 個要求。 </p> </td> 
  </tr> 
 </tbody> 
</table>

**文件更新**

* [實作適用於 Analytics 的 Experience Cloud Identity Service](../implementation-guides/setup-analytics.md#concept-9ebbea85cb844a15b557be572cd142fd)：說明如何使用 [!DNL Analytics] 設定 ID 服務的全新程序。

* [Experience Cloud Identity Service 移轉決策點](../reference/analytics-reference/migration-decisions.md#concept-ba44803eea3c4cc185232a510cec0257)：修訂內容，以求清晰明瞭。使用單一網域意味著，如果您不想再管理資料收集 CNAME，您可以進行移轉。不過，如果您的 CNAME 正常運作，則不需要變更。

## 1.5.3 版 {#section-7c09ba2832bd4644a1ccc3aa83abe66a}

2016 年 1 月

**文件更新**

<table id="table_C1A5DBED6B104C0FBA54EC663D3B0E86"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> 主題 </th> 
   <th colname="col2" class="entry"> 說明 </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <a href="../reference/authenticated-state.md" format="dita" scope="local"> 客戶 ID 和驗證狀態 </a> </p> </td> 
   <td colname="col2"> <p>已修訂文字。客戶 ID 必須以未編碼值的形式傳入。對 ID 進行編碼，將會產生雙重編碼的識別碼。 </p> </td> 
  </tr> 
 </tbody> 
</table>
