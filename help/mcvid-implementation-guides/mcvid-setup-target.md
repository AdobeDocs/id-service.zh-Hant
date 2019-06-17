---
description: 這些指示適用於想使用 Experience Cloud ID 服務但不想使用動態標籤管理 (DTM) 的 Target 客戶。不過，我們強烈建議您使用 DTM 來實施 ID 服務。DTM 可簡化工作流程並自動確保程式碼的放置和順序正確無誤。
keywords: ID 服務
seo-description: 這些指示適用於想使用 Experience Cloud ID 服務但不想使用動態標籤管理 (DTM) 的 Target 客戶。不過，我們強烈建議您使用 DTM 來實施 ID 服務。DTM 可簡化工作流程並自動確保程式碼的放置和順序正確無誤。
seo-title: 實施適用於 Target 的 Experience Cloud ID 服務
title: 實施適用於 Target 的 Experience Cloud ID 服務
uuid: cb3581fa-4c4b-43aa-bb8 e-8db85 a6 a1 ef
translation-type: tm+mt
source-git-commit: bb687c1cd14aae7faef2565dcf9d041a1c06e3bd

---


# 實施適用於 Target 的 Experience Cloud ID 服務{#implement-the-experience-cloud-id-service-for-target}

這些指示適用於想使用 Experience Cloud ID 服務但不想使用動態標籤管理 (DTM) 的 Target 客戶。不過，我們強烈建議您使用 DTM 來實施 ID 服務。DTM 可簡化工作流程並自動確保程式碼的放置和順序正確無誤。

>[!IMPORTANT]
>
>* [先閱讀需求](../mcvid-reference/mcvid-requirements.md)，再開始使用。
>* 先在開發環境中設定與測試此程式碼，然後才在生產中實作。
>



## 步驟1：取得ID服務程式碼 {#section-b32ba0548aa546a79dd38be59832a53e}

需要 [!DNL ID Service]`VisitorAPI.js` 程式碼程式庫。聯絡[客戶服務](https://helpx.adobe.com/marketing-cloud/contact-support.html)以取得此程式碼。

## 步驟2：將Visitor. getInstance函數新增至ID服務程式碼 {#section-287ef2958e9f43858fe9d630ae519e22}

**第 1 部分: 複製下方的 Visitor.getInstance 函數**

```js
var visitor = Visitor.getInstance("INSERT-MARKETING-CLOUD-ORGANIZATION ID-HERE"); 
```

**第 2 部分: 將函數程式碼新增至 VisitorAPI.js 檔案**

將 `Visitor.getInstance` 函數放置在程式碼區塊之後的檔案結尾。您編輯的檔案應該看起來如下所示:

```js
/* 
========== DO NOT ALTER ANYTHING BELOW THIS LINE ========== 
Version and copyright section 
*/ 
 
// Visitor API code library section 
 
// Put Visitor.getInstance at the end of the file, after the code library 
 
var visitor = Visitor.getInstance("INSERT-MARKETING-CLOUD-ORGANIZATION ID-HERE");
```

## 步驟3：將Experience Cloud組織ID新增至Visitor. getInstance {#section-522b1877be9243c39b222859b821f0ce}

`Visitor.getInstance` 在函數中，以 `INSERT-MARKETING-CLOUD-ORGANIZATION ID-HERE`[!DNL Experience Cloud] 您的組織ID取代。如果您不知道組織 ID，可以在 [!DNL Experience Cloud] 管理頁面中找到。另請參閱[管理 - 核心服務](https://marketing.adobe.com/resources/help/en_US/mcloud/admin_getting_started.html)。您編輯的函數看起來可能類似於下列範例。

`var visitor = Visitor.getInstance("1234567ABC@AdobeOrg");`

>[!IMPORTANT]
>
>*請勿* 變更組織ID中的字元大小寫。ID 區分大小寫，需如實使用。

## 步驟4：新增訪客API程式碼至頁面 {#section-02d8dd7678b64a85b5abc1c4ef0845dd}

在檔案參考之前，將 `VisitorAPI.js` 檔案部署至 `<head>` 標記中的網站 `mbox.js` 。[!DNL Experience Cloud] ID服務必須在第一個 [!DNL Target] 網路呼叫產生之前執行。測試並驗證之後，將程式碼移至生產環境。

## 步驟5：測試並部署ID服務程式碼 {#section-e81ee439bb8a4c2abea43d76f3112e9c}

您可以依下列方式進行測試和部署。

**測試並驗證**

若要測試您的 ID 服務實施:

* 檢查托管頁面之網域中的 AMCV Cookie。
* 驗證 `mboxMCGVID` 會出現在 [!DNL Target] 您的請求中，並包含 [!DNL Experience Cloud] ID(MID)。

如需AMCV Cookie和MID的相關資訊，請參閱 [Cookie和Experience Cloud ID服務](../mcvid-introduction/mcvid-cookies.md) 。

**部署**

當程式碼通過測試後，進行部署。

