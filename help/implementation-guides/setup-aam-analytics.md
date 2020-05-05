---
description: 這些指示適用於想使用 Experience Cloud Identity 服務但不想使用 Dynamic Tag Management (DTM) 的 Analytics 和 Audience Manager 客戶。不過，我們強烈建議您使用 DTM 來實作 ID 服務。DTM可簡化實作工作流程，並自動確保正確的程式碼放置和順序。
keywords: ID Service
seo-description: 這些指示適用於想使用 Experience Cloud Identity 服務但不想使用 Dynamic Tag Management (DTM) 的 Analytics 和 Audience Manager 客戶。不過，我們強烈建議您使用 DTM 來實作 ID 服務。DTM可簡化實作工作流程，並自動確保正確的程式碼放置和順序。
seo-title: 實作適用於 Analytics 和 Audience Manager 的 Experience Cloud Identity 服務
title: 實作適用於 Analytics 和 Audience Manager 的 Experience Cloud Identity 服務
uuid: d46050ae-87de-46cc-911b-d6346c7fd511
translation-type: tm+mt
source-git-commit: d2bc0e7fedc4e48d51f5dad158f9f8bfcb0cb4f3

---


# 實作適用於 Analytics 和 Audience Manager 的 Experience Cloud Identity 服務{#implement-the-experience-cloud-id-service-for-analytics-and-audience-manager}

這些指示適用於想使用 Experience Cloud Identity 服務但不想使用 Dynamic Tag Management (DTM) 的 Analytics 和 Audience Manager 客戶。不過，我們強烈建議您使用 DTM 來實作 ID 服務。DTM可簡化實作工作流程，並自動確保正確的程式碼放置和順序。

>[!IMPORTANT]
>
>* [先閱讀需求](../reference/requirements.md)，再開始使用。
>* 此程式需要AppMeasurement。 使用s_code的客戶無法完成此程式。
>* 先在開發環境中設定與測試此程式碼，然後才在生產中實作。
>



## 步驟1: 規劃伺服器端轉送 {#section-880797cc992d4755b29cada7b831f1fc}

除了此處所述步驟以外，使用 [!DNL Analytics] 和 [!DNL Audience Manager] 的客戶也應移轉至伺服器端轉送。Server-side forwarding lets you remove DIL (Audience Manager&#39;s data collection code) and replace it with the [Audience Management Module](https://docs.adobe.com/content/help/en/audience-manager/user-guide/implementation-integration-guides/integration-other-solutions/audience-management-module.html). 如需詳細 [資訊，請參閱伺服器端轉送檔案](https://docs.adobe.com/content/help/en/analytics/admin/admin-tools/server-side-forwarding/ssf.html) 。

遷移至伺服器端轉送需要規劃和協調。 此程式包括對您網站程式碼進行外部變更，以及Adobe必須執行的內部步驟，才能布建您的帳戶。 事實上，許多遷移過程需要並行進行並一起發佈。 您的實作路徑應依照以下事件順序進行:

1. 與您的 [!DNL Analytics] 和 [!DNL Audience Manager] 聯絡人合作，一同規劃 ID 服務與伺服器端轉送移轉。選擇追蹤伺服器是此規劃的重要一部分。

1. Complete the form on the [integrations and provisioning site](https://adobe.allegiancetech.com/cgi-bin/qwebcorporate.dll?idx=X8SVES) to get started.

1. 同時實作 ID 服務與 [!DNL Audience Management Module]。為了正常運作，[!DNL Audience Management Module] (伺服器端轉送) 和 ID 服務必須針對相同的頁面集同時發行。

## 步驟 2: 下載 ID 服務程式碼 {#section-0780126cf43e4ad9b6fc5fe17bb3ef86}

ID 服務需要 `VisitorAPI.js` 程式碼程式庫。若要下載此程式碼程式庫:

1. Go to **[!UICONTROL Admin]** > **[!UICONTROL Code Manager]**.

1. 在「代碼管理器」中，按一下 **[!UICONTROL JavaScript (新)]** 或 **[!UICONTROL JavaScript (舊)]**。即會下載壓縮的程式碼程式庫。

1. 解壓縮程式碼檔案，並開啟 `VisitorAPI.js` 檔案。

## 步驟 3: 將 Visitor.getInstance 函數新增至 ID 服務程式碼 {#section-9e30838b4d0741658a7a492153c49f27}

>[!IMPORTANT]
>
>* 舊版ID服務API將此函式放置在不同的位置，並需要不同的語法。 如果您要從1.4版之前的版 [本移轉](../release-notes/notes-2015.md#section-f5c596f355b14da28f45c798df513572)，請注意此處說明的新位置和語法。
>* ALL CAPS中的代碼是實際值的預留位置。 以您的組織ID、追蹤伺服器URL或其他命名值取代此文字。
>



**第1部分： 複製下方的Visitor.getInstance函式**

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

**第二部分： 將函式程式碼新增至Visitor API.js檔案**

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

在 `Visitor.getInstance` 函數中，將 `INSERT-MARKETING-CLOUD-ORGANIZATION ID-HERE` 取代為 Experience Cloud 組織 ID。如果您不知道組織ID，可在Experience Cloud管理頁面上找到它。 您編輯的函數看起來可能類似於下列範例。

`var visitor = Visitor.getInstance("1234567ABC@AdobeOrg", { ...`

>[!IMPORTANT]
>
>*請勿*&#x200B;變更組織 ID 中的字元大小寫。ID 區分大小寫，需如實使用。

## 步驟 5: 將追蹤伺服器新增至 Visitor.getInstance {#section-0dfc52096ac2427f86045aab9a0e0dfc}

Analytics會使用追蹤伺服器來收集資料。

**第 1 部分: 尋找您的追蹤伺服器 URL**

檢查 `s_code.js` 或 `AppMeasurement.js` 檔案，以尋找追蹤伺服器 URL。您想根據下列變數指定 URL:

* `s.trackingServer`
* `s.trackingServerSecure`

**第二部分： 設定追蹤伺服器變數**

若要決定要使用的追蹤伺服器變數：

1. 回答下面決策表中的問題。 使用與答案對應的變數。
1. 以追蹤伺服器URL取代追蹤伺服器預留位置。
1. 從程式碼中移除未使用的追蹤伺服器和Experience Cloud伺服器變數。

![](assets/tracking-server-matrix.png)

>[!NOTE]
>
>使用時，請將 Experience Cloud 伺服器 URL 與其對應的追蹤伺服器 URL 配對，如下所示:

* Experience Cloud伺服器URL =追蹤伺服器URL
* Experience Cloud伺服器安全URL =追蹤伺服器安全URL

若不清楚如何尋找您的追蹤伺服器，請參閱[常見問題集](../faq-intro/faq.md)和[正確填入 trackingServer 及 trackingServerSecure 變數](https://helpx.adobe.com/tw/analytics/kb/determining-data-center.html#)。

## 步驟 6: 更新您的 AppMeasurement.js 檔案 {#section-5517e94a09bc44dfb492ebca14b43048}

This step requires [!UICONTROL AppMeasurement]. 如果您仍在使用 s_code，將無法繼續。

將下方所示的 `Visitor.getInstance` 函數新增至您的 `AppMeasurement.js` 檔案。將此函數放置在包含設定的相同區段 (例如 `trackDownloads`、`linkInternalFilters`、`charSet` 等)。

`s.visitor = Visitor.getInstance("INSERT-MARKETING-CLOUD-ORGANIZATION ID-HERE");`

>[!IMPORTANT]
>
>此時您應移除 [!DNL Audience Manager] DIL 程式碼，改為使用「對象管理模組」。如需 [指示，請參閱實作伺服器端轉送](https://docs.adobe.com/content/help/en/analytics/admin/admin-tools/server-side-forwarding/ssf.html) 。

***(可選用，但建議使用)*建立自訂 Prop **

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

If any of these use cases apply to your situation, ask [Customer Care](https://helpx.adobe.com/tw/marketing-cloud/contact-support.html) to set up a temporary [grace period](../reference/analytics-reference/grace-period.md). 寬限期最多可執行180天。 如有需要，您可以續約寬限期。

**部分實作**

如果您有使用ID服務的頁面，而有些頁面沒有使用，而且這些頁面都會報告至相同的Analytics報表套裝，則需要寬限期。 如果您有跨網域報告的全域報告套裝，就很常見。

在將ID服務部署在所有報告至相同報告套裝的網頁上後，停止寬限期。

**s_vi Cookie需求**

如果您要求新訪客在移轉至ID服務後擁有s_vi Cookie，則需要寬限期。 如果實作讀取 s_vi Cookie 並將其儲存在變數中，這個情況是很常見的。

當您的實作可擷取 MID，而非讀取 s_vi Cookie 之後，則可停止寬限期。

另請參閱 [Cookie 與 Experience Cloud Identity 服務](../introduction/cookies.md)。

**點擊流資料整合**

如果您將資料從點擊流資料資料源傳送至內部系統，而且該程序使用 `visid_high` 和 `visid_low` 欄位，則需要寬限期。

您的資料擷取程序可使用 `post_visid_high` 和 `post_visid_low` 欄之後，即可停止寬限期。

另請參閱點 [按流資料欄參考](https://docs.adobe.com/content/help/zh-Hant/analytics/export/analytics-data-feed/data-feed-overview.html)。

## 步驟 9: 測試並部署 ID 服務程式碼 {#section-f857542bfc70496dbb9f318d6b3ae110}

您可以依照以下流程進行測試和部署。

**測試和驗證**

若要測試您的 ID 服務實作，請檢查:

* [AMCV Cookie](../introduction/cookies.md)，在托管頁面的網域中。
* Analytics影像要求中的MID值與 [Adobe除錯程式](https://docs.adobe.com/content/help/en/analytics/implementation/validate/debugger.html)。
* 另請參閱[測試及驗證 Experience Cloud Identity 服務](../implementation-guides/test-verify.md)。

若要驗證伺服器端轉送，請參 [閱如何驗證伺服器端轉送實作](https://docs.adobe.com/content/help/en/analytics/admin/admin-tools/server-side-forwarding/ssf-verify.html)。

**部署**

在程式碼通過測試後進行部署。

如果您啟用寬限期：

* 請確定影像要求中包含Analytics ID(AID)和MID。
* 當您符合中止條件時，請記得停用寬限期。

