---
description: 這些指示適用於想使用訪客ID服務但不想使用標籤的Target客戶。 不過，我們強烈建議您使用標籤來實作訪客ID服務。 標記可簡化實作工作流程，並自動確保程式碼放置和順序的正確性。
keywords: 訪客 ID 服務
title: 實作適用於Target的Adobe訪客ID服務
exl-id: 7a387e98-c8fc-4904-942a-be5e527eada2
TQID: https://experienceleague.adobe.com/1994Y39yotvpJkcYazVnG0w-GupHiZZipnLWSTbgle8
product_v2: id: e1971122-7081-4556-9222-8a31bd71800c
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554id: c66ffd68-0f65-42bb-aa23-b4020f12e0bdid: f8a45b24-4be7-4f1b-909b-60d06b483a20id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2: id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87cid: d3cdead0-685a-4489-9250-4bb709942f66id: eddd9b14-83bd-4ff4-9072-54a4a484abb7
source-git-commit: 09ee359440c122702a6ce83708c98af3862c9cc9
workflow-type: tm+mt
source-wordcount: 430
ht-degree: 47%

---

# 實作適用於Target的Adobe訪客ID服務{#implement-the-experience-cloud-id-service-for-target}

這些指示適用於想使用訪客ID服務但不想使用[標籤](https://experienceleague.adobe.com/docs/experience-platform/tags/home.html?lang=zh-Hant)的Target客戶。 不過，我們強烈建議您使用標籤來實作訪客ID服務。 標記可簡化實作工作流程，並自動確保程式碼放置和順序的正確性。

>[!IMPORTANT]
>
>* [先閱讀需求](../reference/requirements.md)，再開始使用。
>* 先在開發環境中設定與測試此程式碼，然後才在生產中實作。

## 步驟1：取得訪客ID服務程式碼 {#section-b32ba0548aa546a79dd38be59832a53e}

訪客ID服務需要`VisitorAPI.js`程式碼程式庫。 連絡[客戶服務](https://helpx.adobe.com/tw/marketing-cloud/contact-support.html)以取得此程式碼。

## 步驟2：將Visitor.getInstance函式新增至Visitor ID服務程式碼 {#section-287ef2958e9f43858fe9d630ae519e22}

**第 1 部分：複製下方的 Visitor.getInstance 函數**

```js
var visitor = Visitor.getInstance("INSERT-IMS-ORG-ID-HERE"); 
```

**第2部分：將函式程式碼新增至`VisitorAPI.js`檔案**

將 `Visitor.getInstance` 函數放置在程式碼區塊之後的檔案結尾。 完成編輯的檔案應該如下所示：

```js
/* 
========== DO NOT ALTER ANYTHING BELOW THIS LINE ========== 
Version and copyright section 
*/ 
 
// Visitor API code library section 
 
// Put Visitor.getInstance at the end of the file, after the code library 
 
var visitor = Visitor.getInstance("INSERT-IMS-ORG-ID-HERE");
```

## 步驟3：將您的IMS組織ID新增至Visitor.getInstance {#section-522b1877be9243c39b222859b821f0ce}

在`Visitor.getInstance`函式中，將`INSERT-IMS-ORG-ID-HERE`取代為您的IMS組織ID。 如果您不知道您的IMS組織ID，可以在CX企業管理頁面上找到。 另請參閱[管理 - 核心服務](https://experienceleague.adobe.com/docs/core-services/interface/manage-users-and-products/admin-getting-started.html?lang=zh-Hant)。 您編輯的函數看起來可能類似於下列範例。

`var visitor = Visitor.getInstance("1234567ABC@AdobeOrg");`

>[!IMPORTANT]
>
>*請勿*&#x200B;變更IMS組織ID中的字元大小寫。 ID 區分大小寫，需如實使用。

## 步驟 4：將訪客 API 程式碼新增至頁面 {#section-02d8dd7678b64a85b5abc1c4ef0845dd}

先將 `VisitorAPI.js` 檔案部署至網站的 `<head>` 標籤中，然後再參照 `mbox.js` 檔案。 訪客ID服務必須在產生第一個Target網路呼叫之前執行。 測試並驗證之後，將程式碼移至生產環境。

## 步驟5：測試並部署訪客ID服務程式碼 {#section-e81ee439bb8a4c2abea43d76f3112e9c}

您可以依照以下流程進行測試和部署。

**測試和驗證**

若要測試您的訪客ID服務實作：

* 在您的頁面託管所在的網域中檢查是否有 AMCV Cookie。
* 確認`mboxMCGVID`出現在您的Target請求中，而且其包含ECID。

如需AMCV Cookie與MID的相關資訊，請參閱[Cookie與訪客ID服務](../introduction/cookies.md)。

**部署**

在程式碼通過測試後加以部署。

