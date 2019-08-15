---
description: 這些指示適用於想使用 Experience Cloud Identity 服務但不想使用 Dynamic Tag Management (DTM) 的 Analytics、Audience Manager 和 Target 客戶。不過，我們強烈建議您使用 DTM 來實作 ID 服務。DTM 可簡化工作流程並自動確保程式碼的放置和順序正確無誤。
keywords: ID 服務
seo-description: 這些指示適用於想使用 Experience Cloud Identity 服務但不想使用 Dynamic Tag Management (DTM) 的 Analytics、Audience Manager 和 Target 客戶。不過，我們強烈建議您使用 DTM 來實作 ID 服務。DTM 可簡化工作流程並自動確保程式碼的放置和順序正確無誤。
seo-title: 實作適用於 Analytics、Audience Manager 和 Target 的 Experience Cloud Identity 服務
title: 實作適用於 Analytics、Audience Manager 和 Target 的 Experience Cloud Identity 服務
uuid: 9d446b77-ca62-4325-8bb0-ff43a52313c0
translation-type: ht
source-git-commit: f7f23d89649a888f5e9d8c94526b550fbda7045b

---


# 實作適用於 Analytics、Audience Manager 和 Target 的 Experience Cloud Identity 服務 {#implement-the-experience-cloud-id-service-for-analytics-audience-manager-and-target}

這些指示適用於想使用 Experience Cloud Identity 服務但不想使用 Dynamic Tag Management (DTM) 的 Analytics、Audience Manager 和 Target 客戶。不過，我們強烈建議您使用 DTM 來實作 ID 服務。DTM 可簡化工作流程並自動確保程式碼的放置和順序正確無誤。

>[!IMPORTANT]
>
>開始前請先參閱 ID 服務[需求](../reference/requirements.md)，並注意本實作專屬的下列需求: &gt;
>* 使用 s_code 的客戶無法完成此程序。請升級至 Mbox 程式碼 v61 版以完成此程序。
>* 請&#x200B;*先*&#x200B;在開發環境中設定與測試此程式碼，然後才在生產環境中實作。
>



## 步驟1: 規劃伺服器端轉送 {#section-880797cc992d4755b29cada7b831f1fc}

除了此處所述步驟以外，使用 [!DNL Analytics] 和 [!DNL Audience Manager] 的客戶也應移轉至伺服器端轉送。伺服器端轉送功能可讓您移除 DIL (Audience Manager 的資料收集程式碼)，並將其取代為[對象管理模組](https://marketing.adobe.com/resources/help/en_US/aam/c_profiles_audiences.html)。如需詳細資訊，請參閱[伺服器端轉送功能文件](https://marketing.adobe.com/resources/help/zh_TW/reference/ssf.html)。

移轉至伺服器端轉送需要規劃與協調。此程序包括對您的網站程式碼進行外部變更，以及 Adobe 佈建您的帳戶所必須進行的內部步驟。事實上，其中許多移轉程序必須同時進行，以及同時發行。您的實作路徑應依照以下事件順序進行:

1. 與您的 [!DNL Analytics] 和 [!DNL Audience Manager] 聯絡人合作，一同規劃 ID 服務與伺服器端轉送移轉。選擇追蹤伺服器是此規劃的重要一部分。

1. 完成[整合與佈建網站](https://adobe.allegiancetech.com/cgi-bin/qwebcorporate.dll?idx=X8SVES)上的表單即可開始使用。

1. 同時實作 ID 服務與 [!DNL Audience Management Module]。為了正常運作，[!DNL Audience Management Module] (伺服器端轉送) 和 ID 服務必須針對相同的頁面集同時發行。

## 步驟 2: 下載 ID 服務程式碼 {#section-0780126cf43e4ad9b6fc5fe17bb3ef86}

ID 服務需要 `VisitorAPI.js` 程式碼程式庫。若要下載此程式碼程式庫:

1. 前往&#x200B;**[!UICONTROL 管理 &gt; 代碼管理器]**。
1. 在「代碼管理器」中，按一下 **[!UICONTROL JavaScript (新)]** 或 **[!UICONTROL JavaScript (舊)**]。即會下載壓縮的程式碼程式庫。

1. 解壓縮程式碼檔案，並開啟 `VisitorAPI.js` 檔案。

## 步驟 3: 將 Visitor.getInstance 函數新增至 ID 服務程式碼 {#section-9e30838b4d0741658a7a492153c49f27}

>[!IMPORTANT]
>
>* 舊版 ID 服務 API 將此函數放置在不同位置，因此需要不同語法。如果您要從 [1.4 版](../release-notes/notes-2015.md#section-f5c596f355b14da28f45c798df513572)之前的版本移轉，請注意此處說明的新位置和語法。
>* 全部大寫的程式碼是實際值的預留位置。請以您的組織 ID、追蹤伺服器 URL 或其他具名值來取代此文字。
>



**第 1 部分: 複製下方的 Visitor.getInstance 函數**

```js
var visitor = Visitor.getInstance("INSERT-MARKETING-CLOUD-ORGANIZATION ID-HERE", { 
     trackingServer: "INSERT-TRACKING-SERVER-HERE", // same as s.trackingServer 
     trackingServerSecure: "INSERT-SECURE-TRACKING-SERVER-HERE", // same as s.trackingServerSecure 
 
     // To enable CNAME support, add the following configuration variables 
     // If you are not using CNAME, DO NOT include these variables 
     marketingCloudServer: "INSERT-TRACKING-SERVER-HERE", 
     marketingCloudServerSecure: "INSERT-SECURE-TRACKING-SERVER-HERE" // same as s.trackingServerSecure 
}); 
```

**第 2 部分: 將函數程式碼新增至 Visitor API.js 檔案**

將 `Visitor.getInstance` 函數放置在程式碼區塊之後的檔案結尾。您編輯的檔案應該看起來如下所示:

```js
/* 
========== DO NOT ALTER ANYTHING BELOW THIS LINE ========== 
Version and copyright section 
*/ 
 
// Visitor API code library section 
 
// Put Visitor.getInstance at the end of the file, after the code library 
 
var visitor = Visitor.getInstance("INSERT-MARKETING-CLOUD-ORGANIZATION ID-HERE", { 
     trackingServer: "INSERT-TRACKING-SERVER-HERE", // same as s.trackingServer 
     trackingServerSecure: "INSERT-SECURE-TRACKING-SERVER-HERE", // same as s.trackingServerSecure 
 
     // To enable CNAME support, add the following configuration variables 
     // If you are not using CNAME, DO NOT include these variables 
     marketingCloudServer: "INSERT-TRACKING-SERVER-HERE", 
     marketingCloudServerSecure: "INSERT-SECURE-TRACKING-SERVER-HERE" // same as s.trackingServerSecure 
}); 
```

## 步驟 4: 將您的 Experience Cloud 組織 ID 新增至 Visitor.getInstance {#section-e2947313492546789b0c3b2fc3e897d8}

在 `Visitor.getInstance` 函數中，將 `INSERT-MARKETING-CLOUD-ORGANIZATION ID-HERE` 取代為 Experience Cloud 組織 ID。如果您不知道組織 ID，可以在 Experience Cloud 管理頁面中找到。您編輯的函數看起來可能類似於下列範例。

`var visitor = Visitor.getInstance("1234567ABC@AdobeOrg", { ...`

>[!IMPORTANT]
>
>*請勿*&#x200B;變更組織 ID 中的字元大小寫。ID 區分大小寫，需如實使用。

## 步驟 5: 將追蹤伺服器新增至 Visitor.getInstance {#section-0dfc52096ac2427f86045aab9a0e0dfc}

Analytics 使用追蹤伺服器來進行資料收集。

**第 1 部分: 尋找您的追蹤伺服器 URL**

檢查 `s_code.js` 或 `AppMeasurement.js` 檔案，以尋找追蹤伺服器 URL。您想根據下列變數指定 URL:

* `s.trackingServer`
* `s.trackingServerSecure`

**第 2 部分: 設定追蹤伺服器變數**

若要確定要使用的追蹤伺服器變數:

1. 回答以下決策矩陣中的問題。使用對應答案的變數。
1. 將追蹤伺服器預留位置取代為您的追蹤伺服器 URL。
1. 將未使用的追蹤伺服器與 Experience Cloud 伺服器變數從程式碼中移除。

![](assets/tracking-server-matrix.png)

>[!NOTE]
>
>使用時，請將 Experience Cloud 伺服器 URL 與其對應的追蹤伺服器 URL 配對，如下所示:

* Experience Cloud 伺服器 URL = 追蹤伺服器 URL
* Experience Cloud 伺服器安全 URL = 追蹤伺服器安全 URL

若不清楚如何尋找您的追蹤伺服器，請參閱[常見問題集](../faq-intro/faq.md)和[正確填入 trackingServer 及 trackingServerSecure 變數](https://helpx.adobe.com/tw/analytics/kb/determining-data-center.html#)。

## 步驟 6: 更新您的 AppMeasurement.js 檔案 {#section-5517e94a09bc44dfb492ebca14b43048}

此步驟需要用到 [!UICONTROL AppMeasurement]。如果您仍在使用 s_code，將無法繼續。

將下方所示的 `Visitor.getInstance` 函數新增至您的 `AppMeasurement.js` 檔案。將此函數放置在包含設定的相同區段 (例如 `trackDownloads`、`linkInternalFilters`、`charSet` 等)。

`s.visitor = Visitor.getInstance("INSERT-MARKETING-CLOUD-ORGANIZATION ID-HERE");`

>[!IMPORTANT]
>
>此時您應移除 [!DNL Audience Manager] DIL 程式碼，改為使用「對象管理模組」。請參閱[實作伺服器端轉送](https://marketing.adobe.com/resources/help/zh_TW/reference/ssf.html)以取得指示。

***(可選用，但建議使用)*建立自訂 Prop**

在 `AppMeasurement.js` 中設定自訂 prop 以測量涵蓋範圍.將此自訂 Prop 新增至 `doPlugins` 檔案的 `AppMeasurement.js` 函數:

```js
// prop1 is used as an example only. Choose any available prop. 
s.prop1 = (typeof(Visitor) != "undefined" ? "VisitorAPI Present" : "VisitorAPI Missing");
```

## 步驟 7: 將訪客 API 程式碼新增至頁面 {#section-c2bd096a3e484872a72967b6468d3673}

將 ` [!UICONTROL VisitorAPI.js]` 檔案放入每個頁面的 `<head>` 標籤中。將 `VisitorAPI.js` 檔案放到頁面中時:

* 放在 `<head>` 區段的開頭處，使其出現在其他解決方案標籤的前面。
* 必須在 AppMeasurement 及其他 [!DNL Experience Cloud] 解決方案的程式碼之前執行此檔案。

## 步驟 8: (選用) 設定寬限期 {#section-aceacdb7d5794f25ac6ff46f82e148e1}

若其中有任何使用案例適用於您的情況，請要求[客戶服務](https://helpx.adobe.com/tw/marketing-cloud/contact-support.html)設定暫時的[寬限期](../reference/analytics-reference/grace-period.md)。寬限期可執行最多 180 天。您可以視需要更新寬限期。

**部分實作**

如果部分頁面使用 ID 服務，部分頁面未使用，且這些頁面全部都向相同的 Analytics 報表套裝報告，則您需要寬限期。如果您的全域報表套裝可針對不同網域提出報告，這個情況是很常見的。

當 ID 服務已部署在報告至相同報表套裝的所有網頁之後，則可停止寬限期。

**s_vi Cookie 需求**

如果您要求新訪客在移轉至 ID 服務之後擁有 s_vi Cookie，則需要寬限期。如果實作讀取 s_vi Cookie 並將其儲存在變數中，這個情況是很常見的。

當您的實作可擷取 MID，而非讀取 s_vi Cookie 之後，則可停止寬限期。

另請參閱 [Cookie 與 Experience Cloud Identity 服務](../introduction/cookies.md)。

**點擊流資料整合**

如果您將資料從點擊流資料資料源傳送至內部系統，而且該程序使用 `visid_high` 和 `visid_low` 欄位，則需要寬限期。

您的資料擷取程序可使用 `post_visid_high` 和 `post_visid_low` 欄之後，即可停止寬限期。

另請參閱[點按流資料欄參考](https://marketing.adobe.com/resources/help/zh_TW/sc/clickstream/datafeeds_reference.html)。

## 步驟 9: 測試並驗證 {#section-f857542bfc70496dbb9f318d6b3ae110}

本實作中的 [!DNL Experience Cloud] 解決方案會以機碼值組的形式傳回 ID。每個解決方案使用不同的機碼 (例如 [!DNL Analytics] SDID、[!DNL Target] mboxMCSDID) 來保存相同的 ID。若要測試實作，請在開發環境中載入您的頁面。使用監控 HTTP 要求和回應的瀏覽器主控台或軟體，來檢查下表中列出的 ID。如果下列機碼值組傳回相同的 ID 值，代表已正確實作 ID 服務。

>[!TIP]
>
>您可以使用 [Adobe Debugger](https://marketing.adobe.com/resources/help/zh_TW/sc/implement/?f=debugger.html) 或 [Charles HTTP Proxy](https://www.charlesproxy.com/) 來檢查這些解決方案專屬的 ID。不過，您當然可以使用最適合您的任何工具或偵錯工具。

**所有解決方案**

檢查下列項目:

* [AMCV Cookie](../introduction/cookies.md)，在托管頁面的網域中。
* [!DNL Experience Cloud] ID (MID) 搭配 [!DNL Adobe] 偵錯工具或您慣用的偵錯工具。

如需可協助您判斷 ID 服務是否正常運作的其他檢查，請參閱[測試及驗證 Experience Cloud Identity 服務](../implementation-guides/test-verify.md)。

**Analytics**

檢查 JavaScript 要求中的 SDID 識別碼。Analytics SDID 應符合 Target mboxMCSDID。

如果測試傳回 AID，代表下列其中一種情形:

* 您在移轉舊版 [!DNL Analytics] ID 的程序中傳回訪客。
* 您已啟用[寬限期](../reference/analytics-reference/grace-period.md)。

如果看到 AID，請根據 [!DNL Target] mboxMCAVID 檢查其值。如果有正確實作 ID 服務，這些值會相同。

**Audience Manager**

若要測試伺服器端轉送，請參閱:

* [如何判斷您的帳戶是否準備就緒，已可接收轉送的資料](https://marketing.adobe.com/resources/help/en_US/aam/ssf-success.html)
* [如何判斷您的帳戶是否準備好接收轉送的資料](https://marketing.adobe.com/resources/help/en_US/aam/ssf-fail.html)

**Target**

檢查下列項目:

* mboxMCGVID
* mboxMCSDID (mboxMCSDID 應符合 Analytics SDID)。

如果測試傳回 mboxMCAVID，代表下列其中一種情形:

* 您在移轉舊版 [!DNL Analytics] ID 的程序中傳回訪客。
* 您已啟用寬限期。

如果看到 mboxMCAVID，請根據 [!DNL Analytics] AID 檢查其值。如果有正確實作 ID 服務，這些值會相同。

**部署工作**

## 步驟 10: 部署 {#section-4188fa95e7dc455a986b48a6c517c1c9}

當程式碼通過測試後，進行部署。

如果您已啟用寬限期:

* 請確保 Analytics ID (AID) 與 MID 位於影像請求中。
* 當您符合[中止條件](../implementation-guides/setup-aam-analytics-target.md#section-aceacdb7d5794f25ac6ff46f82e148e1)時，請記得停用寬限期。

