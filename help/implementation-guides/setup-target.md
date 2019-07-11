---
description: 這些指示適用於想使用 Experience Cloud ID 服務但不想使用動態標籤管理 (DTM) 的 Target 客戶。不過，我們強烈建議您使用 DTM 來實作 ID 服務。DTM 可簡化工作流程並自動確保程式碼的放置和順序正確無誤。
keywords: ID 服務
seo-description: 這些指示適用於想使用 Experience Cloud ID 服務但不想使用動態標籤管理 (DTM) 的 Target 客戶。不過，我們強烈建議您使用 DTM 來實作 ID 服務。DTM 可簡化工作流程並自動確保程式碼的放置和順序正確無誤。
seo-title: 實作適用於 Target 的 Experience Cloud ID 服務
title: 實作適用於 Target 的 Experience Cloud ID 服務
uuid: cb3581fa-4c4b-43aa-bb8e-8db85a6a1ef2
translation-type: ht
source-git-commit: 3e7b49564938527e1b6bca3a5fbaf9eb141d2e06

---


# 實作適用於 Target 的 Experience Cloud ID 服務{#implement-the-experience-cloud-id-service-for-target}

這些指示適用於想使用 Experience Cloud ID 服務但不想使用動態標籤管理 (DTM) 的 Target 客戶。不過，我們強烈建議您使用 DTM 來實作 ID 服務。DTM 可簡化工作流程並自動確保程式碼的放置和順序正確無誤。

>[!IMPORTANT]
>
>* [先閱讀需求](../reference/requirements.md)，再開始使用。
>* 先在開發環境中設定與測試此程式碼，然後才在生產中實作。
>



## 步驟 1: 取得 ID 服務程式碼 {#section-b32ba0548aa546a79dd38be59832a53e}

[!DNL ID Service]需要 `VisitorAPI.js` 程式碼程式庫。請聯絡[客戶服務](/content/help/tw/zh-Hant/marketing-cloud/contact-support.html)以取得此程式碼。

## 步驟 2: 將 Visitor.getInstance 函數新增至 ID 服務程式碼 {#section-287ef2958e9f43858fe9d630ae519e22}

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

## 步驟 3: 將您的 Experience Cloud 組織 ID 新增至 Visitor.getInstance {#section-522b1877be9243c39b222859b821f0ce}

在 `Visitor.getInstance` 函數中，將 `INSERT-MARKETING-CLOUD-ORGANIZATION ID-HERE` 取代為 [!DNL Experience Cloud] 組織 ID。如果您不知道組織 ID，可以在 [!DNL Experience Cloud] 管理頁面中找到。另請參閱[管理員 -核心服務](https://marketing.adobe.com/resources/help/zh_TW/mcloud/admin_getting_started.html)。您編輯的函數看起來可能類似於下列範例。

`var visitor = Visitor.getInstance("1234567ABC@AdobeOrg");`

>[!IMPORTANT]
>
>*請勿*變更組織 ID 中的字元大小寫。ID 區分大小寫，需如實使用。

## 步驟 4: 將訪客 API 程式碼新增至頁面 {#section-02d8dd7678b64a85b5abc1c4ef0845dd}

先將 `VisitorAPI.js` 檔案部署至網站的 `<head>` 標籤中，然後再參照 `mbox.js` 檔案。必須在產生第一個 [!DNL Experience Cloud] 網路呼叫之前執行 [!DNL Target] ID 服務。測試並驗證之後，將程式碼移至生產環境。

## 步驟 5: 測試並部署 ID 服務程式碼 {#section-e81ee439bb8a4c2abea43d76f3112e9c}

您可以依照以下流程進行測試和部署。

**測試和驗證**

若要測試您的 ID 服務實作:

* 檢查托管頁面之網域中的 AMCV Cookie。
* 驗證 `mboxMCGVID` 是否顯示在您的 [!DNL Target] 請求中，而且其是否包含 [!DNL Experience Cloud] ID (MID)。

請參閱 [Cookie 與 Experience Cloud ID](../introduction/cookies.md)，以瞭解有關 AMCV Cookie 與 MID 的資訊。

**部署**

當程式碼通過測試後，進行部署。

