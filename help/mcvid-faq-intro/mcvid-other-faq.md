---
description: 關於搭配 ID 服務使用其他 Experience Cloud 解決方案的功能、功用和問題之常見問題集。
keywords: ID 服務
seo-description: 關於搭配 ID 服務使用其他 Experience Cloud 解決方案的功能、功用和問題之常見問題集。
seo-title: 其他Experience Cloud解決方案的常見問答集
title: 其他Experience Cloud解決方案的常見問答集
uuid: 7d848663-6cbb-4d80-ab06-7b6 d2 dc20 e2 b
translation-type: tm+mt
source-git-commit: bb687c1cd14aae7faef2565dcf9d041a1c06e3bd

---


# 其他Experience Cloud解決方案的常見問答集{#faqs-for-other-experience-cloud-solutions}

關於搭配 ID 服務使用其他 Experience Cloud 解決方案的功能、功用和問題之常見問題集。

## Dynamic Tag Management (DTM) {#section-7ac4b9c1f1fd45a5a03eac3fb5968af7}

**我是否可使用「動態標籤管理」來部署訪客 ID 服務?**

可以，這是慣用和推薦的部署選項。

請參閱[透過 DTM 實現的標準實施](../mcvid-implementation-guides/mcvid-standard.md#concept-89cd0199a9634fc48644f2d61e3d2445)。

## Analytics 與 Audience Manager {#section-b3dd206d497041acb04554c6fb1c912a}

**在我實作 Experience Cloud ID 服務後，使用者的瀏覽歷史記錄會從[!DNL Adobe Analytics]匯出到[!DNL Audience Manager]嗎?**

您有兩個選擇:

* 如果在 ID 服務實作之後，使用者有任何瀏覽活動，使用者和其歷史記錄會包含在匯出至 [!DNL Audience Manager] 的資料中。
* 如果在 ID 服務實作之後，使用者沒有任何瀏覽活動，使用者和其歷史記錄不會包含在匯出至 Audience Manager 的資料中。因為沒有新活動，我們無法將 Analytics ID 與 Experience Cloud ID 建立關聯。

