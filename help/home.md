---
description: Adobe訪客ID服務可為CX Enterprise應用程式和服務啟用共同識別架構。 其運用方式為指派唯一、持續存在的ID （稱為ECID）給網站訪客。
keywords: 訪客ID服務；ECID
title: Adobe訪客ID服務
exl-id: fe1368db-06ca-4c79-b655-b7064e316d74
TQID: https://experienceleague.adobe.com/xzEgzuN2NnyOnhCPocQikOXHFRU6zmLWLGdrJL4C3GM
product_v2: id: e1971122-7081-4556-9222-8a31bd71800c
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554id: c66ffd68-0f65-42bb-aa23-b4020f12e0bdid: f8a45b24-4be7-4f1b-909b-60d06b483a20id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2: id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87cid: f4e6943a-c91a-4134-a2c7-f4f20cfff2f0
source-git-commit: 09ee359440c122702a6ce83708c98af3862c9cc9
workflow-type: tm+mt
source-wordcount: 433
ht-degree: 26%

---

# Adobe訪客ID服務 {#experience-cloud-id-service}

>[!BEGINSHADEBOX]

訪客ID服務&#x200B;**不是** [Experience Platform身分識別服務](https://experienceleague.adobe.com/docs/experience-platform/identity/home.html?lang=zh-Hant)。 訪客ID服務是本指南中說明的`VisitorAPI.js` JavaScript資料庫，可設定Adobe Analytics、Audience Manager和Target的ECID。 如果您正在尋找Adobe Experience Platform服務，此服務會將跨裝置和系統的身分解析為統一的客戶設定檔，請改為參閱[Experience Platform Identity Service概觀](https://experienceleague.adobe.com/docs/experience-platform/identity/home.html?lang=zh-Hant)。

>[!ENDSHADEBOX]

Adobe訪客ID服務可為CX Enterprise應用程式和服務啟用共同識別架構。 其運用方式為指派唯一、持續存在的ID （稱為ECID）給網站訪客。

## 了解身分識別的主要實體

若要更進一步瞭解Adobe如何有助於唯一地識別訪客並解析身分資訊，請閱讀以下劃分：

* **訪客ID服務**：訪客ID服務&#x200B;**負責設定ECID**。 如需詳細資訊，請閱讀[訪客ID服務總覽](./introduction/overview.md)。
* **ECID**： ECID是跨Adobe Experience Platform和Adobe CX Enterprise應用程式使用的共用身分名稱空間，用於識別人員和裝置。 如需有關 ECID 的詳細資訊，請閱讀 [ECID 概觀](https://experienceleague.adobe.com/en/docs/experience-platform/identity/features/ecid)。
* **Experience Platform 身分識別服務**：Experience Platform 身分識別服務透過跨裝置和系統橋接身分，為您提供客戶及其行為的全面視野。 如需詳細資訊，請閱讀 [Experience Platform 身分識別服務概觀](https://experienceleague.adobe.com/docs/experience-platform/identity/home.html?lang=zh-Hant)。

## 開始使用

* [訪客ID服務概述](introduction/overview.md)：瞭解訪客ID服務的功用，以及它如何融入CX Enterprise。
* [訪客ID服務的需求](reference/requirements.md)：在實作訪客ID服務之前，請確認您的解決方案和程式碼程式庫符合先決條件。
* [實作方法](implementation-guides/implementation-methods.md)：比較使用[標籤](https://experienceleague.adobe.com/docs/experience-platform/tags/home.html?lang=zh-Hant)的標準實作與非標準的直接整合方法。

## 探索文件

**實施**

* [實作指南](implementation-guides/implementation-guides.md)
* [與訪客ID服務直接整合](implementation-guides/direct-integration.md)
* [選擇加入服務概述](implementation-guides/opt-in-service/optin-overview.md)
* [測試及驗證訪客ID服務](implementation-guides/test-verify.md)

**API 參考資料**

* [訪客ID服務API概述](library/library.md)
* [getVisitorValues](library/get-set/getvisitorvalues.md)
* [idSyncContainerID](library/function-vars/idsyncontainerid.md)

**常見問題集**

* [訪客ID服務常見問題](faq-intro/faq.md)
* [其他CX企業解決方案的常見問題集](faq-intro/other-faq.md)

## 其他資源

* GitHub上的[ECID JavaScript程式庫發行版本](https://github.com/Adobe-Marketing-Cloud/id-service/releases)
* [訪客ID服務發行說明](release-notes/notes-2022.md)
* [Adobe隱私權中心](https://www.adobe.com/tw/privacy.html)
* [Adobe CX Enterprise檔案](https://experienceleague.adobe.com/docs/home.html?lang=zh-Hant)

