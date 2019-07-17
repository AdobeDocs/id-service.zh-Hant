---
description: 較舊的實施使用動態標籤管理(DTM)來設定、部署和整合Experience Cloud Identity Service與其他Experience Cloud解決方案。
keywords: ID 服務
seo-description: 較舊的實施使用動態標籤管理(DTM)來設定、部署和整合Experience Cloud Identity Service與其他Experience Cloud解決方案。
seo-title: 透過動態標籤管理來實作
title: 透過動態標籤管理來實作
uuid: c4f752c4-392e-4909-b178-911706857064
translation-type: tm+mt
source-git-commit: e6d65f1bfed187d7440512e8f3c2de0550506c95

---


# 透過動態標籤管理來實作{#implementation-with-dynamic-tag-management}

較舊的實施使用動態標籤管理(DTM)來設定、部署和整合Experience Cloud Identity Service與其他Experience Cloud解決方案。

## 透過動態標籤管理來實作{#topic-6f4ed5d96977406ca991e50f3fbd5b01}

較舊的實施使用動態標籤管理(DTM)來設定、部署和整合Experience Cloud Identity Service與其他Experience Cloud解決方案。

>[!NOTE]
>
>Currently, [Adobe Experience Platform Launch](https://docs.adobelaunch.com/) is the preferred and recommended implementation tool because it helps simplify complex tag management tasks and automates code placement beyond the capabilities of DTM. 請參閱[透過 Launch 實作](../implementation-guides/ecid-implement-with-launch.md)。

## 動態標籤管理和 ID 服務 {#section-4a4c4fac5d0a4cbbaff8e1833f73657c}

[動態標籤管理](https://marketing.adobe.com/resources/help/en_US/dtm/) 可讓您設定、部署和管理ID服務例項以及相關 [!DNL Experience Cloud] 的解決方案整合。DTM 可與 ID 服務及其他 Experience Cloud 解決方案深入整合，因此有助於簡化實作程序。只需新增與設定 Experience Cloud ID 工具並指定相關資訊，例如:

* Experience Cloud 組織 ID (若已連結至 Experience Cloud 會自動填入)
* Analytics 追蹤伺服器 (安全和不安全)
* Experience Cloud 伺服器 (適用於第一方追蹤伺服器)

DTM 免費提供給所有 [!DNL Experience Cloud] 客戶使用。

**DTM 快速入門**

DTM 是簡單且功能強大的工具。如果您尚未使用過 DTM，強烈建議您試用看看。請參閱 DTM [文件](https://marketing.adobe.com/resources/help/en_US/dtm/c_overview.html)和 [DTM 入門影片](https://marketing.adobe.com/resources/help/en_US/dtm/jump-start-videos.html)，開始使用本服務。如需使用 DTM 設定 ID 服務的相關指示，請參閱以下章節中的資訊和程序。

## 部署準則 {#concept-54a2ec49af8f4bfca9207b1d404e8e1a}

請先檢閱這些要求和程序，然後再嘗試使用動態標籤管理(DTM)實作Experience Cloud Identity Service。

<!--
mcvid-dtm-deployment.xml
-->

**佈建您的帳戶**

開始之前，請確定已針對 [!DNL Experience Cloud] 佈建組織和解決方案，而且您熟悉[!DNL Dyanamic Tag Management]。本文可協助您快速入門:

* [啓用核心服務的解決方案](https://marketing.adobe.com/resources/help/en_US/mcloud/core_services.html)：實作Experience Cloud並成為管理員。此程序會針對核心服務 (例如客戶屬性和 Experience Cloud 受眾) 導入最新的解決方案。
* [動態標籤管理快速入門](https://marketing.adobe.com/resources/help/en_US/dtm/get_started.html)
* [跳至影片](https://marketing.adobe.com/resources/help/en_US/dtm/jump-start-videos.html)：一系列展示如何執行基本DTM工作的短片。

**ID 服務程式碼放置和載入順序**

ID 服務的運作方式是向 [!DNL Adobe] 資料收集伺服器要求和接收唯一 ID。為了正常運作，您的 ID 服務程式碼必須是:

* 頁面上執行之 [!DNL Adobe] 程式碼的第一個區塊。
* 盡可能放置在頁面最高處，通常位在 `<head>` 程式碼區塊中。

只要您在 DTM 中維護所有的 [!DNL Adobe] 解決方案和程式碼程式庫，就能確保您的 ID 服務程式碼放置在正確位置並於正確時間觸發。

**驗證地區資料收集**

Customers must provide a CNAME or use [!DNL *.sc.omtrdc] for [regional data collection](https://marketing.adobe.com/resources/help/en_US/whitepapers/rdc/) (RDC). 向 [!DNL Adobe] 顧問索取專屬的 RDC 設定。

**設定 Analytics 報表套裝**

新 [!DNL Analytics] 客戶應為資料收集[建立報表套裝](https://marketing.adobe.com/resources/help/en_US/reference/new_report_suite.html)。

## Implement the Experience Cloud Identity Service with DTM {#task-a659cf19dea84ad48edabe0b72ef9f5c}

請依照這些步驟來透過動態標籤管理 (DTM) 實作 ID 服務。

**必要條件**

* 啟用您的 [!DNL Experience Cloud] 解決方案並確認您擁有管理員權限。See [Enable your solutions for core services](https://marketing.adobe.com/resources/help/en_US/mcloud/core_services.html).

* 在 DTM 中建立 Web 屬性。請參閱 DTM [建立 Web 屬性](https://marketing.adobe.com/resources/help/en_US/dtm/web_property.html)文件或[管理員入門影片](https://marketing.adobe.com/resources/help/en_US/dtm/admin-jump-start.html)。

<!--
mcvid-dtm-implement.xml
-->

**實作步驟**&#x200B;若要使用 DTM 實作 ID 服務:

1. 在 DTM [!DNL Dashboard] 中，按一下您要使用的 Web 屬性。
1. 在您選定 Web 屬性的&#x200B;**[!UICONTROL 概述]**&#x200B;標籤中，按一下&#x200B;**[!UICONTROL 新增工具]**。
1. In the **[!UICONTROL Tool Type]** list, click **[!UICONTROL Experience Cloud Identity Service]**.

   >[!NOTE]
   >
   >此動作會使用您的組織 ID 填入 **[!UICONTROL Experience Clould 組織 ID]**&#x200B;方塊。如果 DTM 帳戶未連結至 [!DNL Experience Cloud]，您必須提供此 ID。若要連結帳戶，請參閱[在 Experience Cloud 中連結帳戶](https://marketing.adobe.com/resources/help/en_US/mcloud/organizations.html)。如需如何找到組織 ID 的相關資訊，請參閱[需求](../reference/requirements.md#section-a02f537129a64ffbb690d5738d360c26)。

1. 在&#x200B;**[!UICONTROL 追蹤伺服器]**&#x200B;方塊中輸入追蹤伺服器的名稱。If you're not sure how to find your tracking server see the [FAQ](../faq-intro/faq.md) and [Correctly Populate the trackingServer and trackingServerSecure variables](https://helpx.adobe.com/analytics/kb/determining-data-center.html#).
1. 按一下&#x200B;**[!UICONTROL 建立工具]**&#x200B;和&#x200B;**[!UICONTROL 儲存變更]**。

   儲存後，就會將 ID 服務設定為 DTM 中的工具。不過，此工具尚未可供使用。DTM 工具仍需經過 DTM 發佈/核准程序，您也可以設定其他參數。如需 DTM 核准程序的相關資訊，請參閱[使用者基本入門](https://marketing.adobe.com/resources/help/en_US/dtm/user-basics-jump-start.html)影片。如需可新增至 DTM 之其他參數的相關資訊，請參閱[適用於DTM的Experience Cloud身分服務設定](../implementation-guides/standard.md#concept-fb6cb6a0e6cc4f10b92371f8671f6b59)。

>[!MORE_LIKE_THIS]
>
>* [Web 屬性](https://marketing.adobe.com/resources/help/en_US/dtm/web_property.html)


## Experience Cloud Identity Service Settings for DTM {#concept-fb6cb6a0e6cc4f10b92371f8671f6b59}

說明 [!DNL Organization ID]、[!DNL General] 和 [!DNL Customer Settings] 欄位及如何用於 [!DNL Experience Cloud] ID 服務。

<!--
mcvid-dtm-settings.xml
-->

## 如何找到這些設定? {#section-c5b2d1c928944ae2b8565c1b182fe575}

您在動態標籤管理 (DTM) 中新增並儲存 ID 服務做為工具後，就能使用這些設定。您也可按一下 DTM Web 屬性之[!DNL Installed Tools]區段中的齒輪圖示，來存取這些設定。

![](assets/installedTools.png)

## 組織 ID {#section-949b5a0d8af940558b04ff675cf53f77}

這是與您佈建之 [!DNL Experience Cloud] 公司關聯的必要 ID。組織是可讓管理員設定使用者、群組，以及控制 [!DNL Experience Cloud] 中單一登入存取的實體。組織 ID 是 24 個字元的英數字串，後面接著 (而且必須包含) @AdobeOrg。[!DNL Experience Cloud] 管理員可以在 [「Experience Cloud &gt; 工具」](https://marketing.adobe.com/resources/help/en_US/mcloud/admin_getting_started.html)中找到此 ID。

![](assets/orgID.png)

See also [Cookies and the Experience Cloud Identity Service](../introduction/cookies.md).

## 一般設定 {#section-071d358e40f84629a8901b893dd61392}

這些設定可讓您指定追蹤伺服器、程式碼版本以及新增其他變數。

![](assets/generalSettings.png)

下表列出並定義[!DNL General]設定。

**自動要求訪客 ID**

When checked, dynamic tag management to automatically calls the `getMarketingCloudVisitorID()` method before loading any of the Adobe solutions that use the Experience Cloud Identity Service.

請參閱 [getMarketingCloudVisitorID](../library/get-set/getmcvid.md)。

**Analytics 追蹤伺服器**

Analytics 資料收集所用的追蹤伺服器的名稱。這是寫入影像要求和 Cookie 的網域 (例如 [!DNL http://site.omtrdc.net])。

如果您不知道追蹤伺服器 URL，請查看 `s_code.js` 或 `AppMeasurement.js` 檔案。請利用 `s.trackingServer` 變數設定 URL。

請參閱 [ trackingServer](https://marketing.adobe.com/resources/help/en_US/sc/implement/trackingServer.html) 和[正確填入 trackingServer 和 trackingServerSecure 變數](https://helpx.adobe.com/analytics/kb/determining-data-center.html#)。

**追蹤伺服器安全**

Analytics 資料收集所用的安全追蹤伺服器的名稱。這是寫入影像要求和 Cookie 的網域 (例如 [!DNL https://site.omtrdc.net])。

如果您不知道追蹤伺服器 URL，請查看 `s_code.js` 或 `AppMeasurement.js` 檔案。請利用 `s.trackingServerSecure` 變數設定 URL。

請參閱 [ trackingServer](https://marketing.adobe.com/resources/help/en_US/sc/implement/trackingServer.html) 和[正確填入 trackingServer 和 trackingServerSecure 變數](https://helpx.adobe.com/analytics/kb/determining-data-center.html#)。

**Experience Cloud 伺服器**

如果您的公司使用第一方資料收集 (CNAME) 來在第三方內容中利用第一方 Cookie，請在這裡輸入追蹤伺服器 (例如 [!DNL http://metrics.company.com])。

**Experience Cloud 伺服器安全性**

如果您的公司使用第一方資料收集 (CNAME) 來在第三方內容中利用第一方 Cookie，請在這裡輸入追蹤伺服器 (例如 [!DNL https://metrics.company.com])。

**程式庫版本**

設定您想使用的 ID 服務程式碼程式庫的版本 (`VisitorAPI.js`)。您無法編輯這些功能表選項。

**設定**

這些欄位可讓您新增[函數變數](../library/function-vars/function-vars.md)做為機碼值組。按一下&#x200B;**[!UICONTROL 「新增」]，新增一或多個變數至 ID 服務實作。**

![](assets/dtmVars.png)

>[!IMPORTANT]
>
>在此設定 `cookieDomain` 變數。多部分、頂級網域需要此變數，其中 URL 的最後 2 個部分大於兩個字元。請參閱上方連結中的「設定變數」文件。

## 客戶設定 {#section-238d1272c1504d148fe38fb0ae5d71c2}

可讓您新增整合代碼或已驗證狀態的其他欄位。

![](assets/customerSettings.png)

**整合代碼**

整合代碼是客戶提供的唯一 ID。整合代碼應包含您在 [ 中用來](https://marketing.adobe.com/resources/help/en_US/aam/create-datasource.html)建立資料來源[!DNL Audience Manager]的值。

**值**

此值應該是包含使用者 ID 的資料元素。資料元素是動態值的合適容器，例如來自用戶端特定內部系統的 ID。

**驗證狀態**

可根據訪客的驗證狀態 (例如，登入、登出) 來識別訪客的選項。請參閱[客戶 ID 和驗證狀態](../reference/authenticated-state.md)。

## Test and verify the Experience Cloud Identity Service {#concept-644fdbef433b46ba9c0634ac95eaa680}

這些指示、工具和程序可協助您判斷 ID 服務是否正確運作。這些測試適用於一般的 ID 服務，以及不同的 ID 服務與 [!DNL Experience Cloud] 解決方案組合。

<!--
mcvid-test-verify.xml
-->

## 開始之前 {#section-b1e76ad552ed4eb793b6e521a55127d4}

開始測試及驗證 ID 服務前的重要須知。

**瀏覽器環境**

在一般瀏覽器工作階段中進行測試時，在每次測試前請先清除瀏覽器快取。

或者，您也可以在匿名或無痕式瀏覽器工作階段中測試 ID 服務。在匿名工作階段中，每次測試前無須清除瀏覽器 Cookie 或快取。

**工具**

[Adobe 偵錯工具](https://marketing.adobe.com/resources/help/en_US/sc/implement/debugger.html)和 [Charles HTTP Proxy](https://www.charlesproxy.com/) 可協助您判斷 ID 服務是否已設定為正確地搭配 Analytics 運作。本節中的資訊是以 Adobe 偵錯工具和 Charles 傳回的結果為主。不過，您當然可以使用最適合您的任何工具或偵錯工具。

## 使用 Adobe 偵錯工具進行測試 {#section-861365abc24b498e925b3837ea81d469}

如果您在 [!DNL Experience Cloud ID] 偵錯工具回應中看到 [!DNL Adobe] (MID)，代表您的服務整合已正確設定。See [Cookies and the Experience Cloud Identity Service](../introduction/cookies.md) for more information about the MID.

若要使用 [!DNL Adobe][ 偵錯工具驗證 ID 服務的狀態](https://marketing.adobe.com/resources/help/en_US/sc/implement/debugger.html):

1. 清除瀏覽器 Cookie 或開啟匿名瀏覽工作階段。
1. 載入包含 ID 服務程式碼的測試頁面。
1. 開啟 [!DNL Adobe] 偵錯工具。
1. 查看 MID 的結果。

## 瞭解 Adobe Debugger 的結果 {#section-bd2caa6643d54d41a476d747b41e7e25}

MID 儲存在使用下列語法的機碼-值組中: `MID= *`Experience Cloud ID`*`。偵錯工具會顯示此項資訊，如下所示。

**成功**

如果您看到類似以下的回應，代表 ID 服務已正確實作:

```
mid=20265673158980419722735089753036633573
```

如果您是 [!DNL Analytics] 客戶，則除了 MID，還可能看到 [!DNL Analytics] ID (AID)。這可能發生在下列情形:

* 某些早期/長期網站訪客。
* 您已啟用寬限期。

**失敗**

如果偵錯工具發生下列情形，請聯絡[客戶服務](https://helpx.adobe.com/marketing-cloud/contact-support.html):

* 無法傳回 MID。
* 傳回錯誤訊息，指出您的 ID 尚未佈建。

## 使用 Charles HTTP Proxy 進行測試 {#section-d9e91f24984146b2b527fe059d7c9355}

若要使用 Charles 驗證 ID 服務的狀態:

1. 清除瀏覽器 Cookie 或開啟匿名瀏覽工作階段。
1. 啟動 Charles。
1. 載入包含 ID 服務程式碼的測試頁面。
1. 查看要求和回應呼叫，以及下方所述的資料。

## 瞭解 Charles 的結果 {#section-c10c3dc0bb9945cbaffcf6fec7082fab}

請參閱本節以了解當您使用 Charles 監控 HTTP 呼叫時，應至何處查看哪些項目。

**Charles 中的成功 ID 服務要求**

當 `Visitor.getInstance` 函數對 `dpm.demdex.net` 進行 JavaScript 呼叫時，表示您的 ID 服務程式碼正常運作。成功的要求包含[組織 ID](../reference/requirements.md#section-a02f537129a64ffbb690d5738d360c26)。組織 ID是以使用下列語法的機碼-值組來傳遞: `d_orgid= *`organization ID`*`。查看 `dpm.demdex.net` 標籤下方的 [!DNL Structure] 和 JavaScript 呼叫。查看 [!DNL Request] 標籤下方的組織 ID。

![](assets/charles_request.png)

**Charles 中的成功 ID 服務回應**

當[資料收集伺服器](https://marketing.adobe.com/resources/help/en_US/aam/c_compcollect.html) (DCS) 的回應傳回 MID 時，表示您的帳戶已正確佈建。MID 是以使用下列語法的機碼-值組傳回: `d_mid: *`visitor Experience Cloud ID`*`。查看 [!DNL Response] 標籤中的 MID，如下所示。

![](assets/charles_response_success.png)

**Charles 中的失敗 ID 服務回應**

如果 DCS 回應中缺少 MID，表示您的帳戶未正確佈建。失敗的回應會在 [!DNL Response] 標籤中傳回錯誤碼和訊息，如下所示。如果您在 DCS 回應中看到這個錯誤訊息，請聯絡客戶服務。

![](assets/charles_response_unsuccessful.png)

如需錯誤碼的相關詳細資訊，請參閱 [DCS 錯誤碼、訊息和範例](https://marketing.adobe.com/resources/help/en_US/aam/dcs_error_codes.html)。
