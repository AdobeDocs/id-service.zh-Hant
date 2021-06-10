---
description: 關於搭配 ID 服務使用其他 Experience Cloud 解決方案的功能、功用和問題之常見問題集。
keywords: ID 服務
title: 其他 Experience Cloud 解決方案的常見問題集
exl-id: d1164951-01c9-4375-981a-f87d8a280e4b
source-git-commit: 06e935a4ba4776baa900d3dc91e294c92b873c0f
workflow-type: tm+mt
source-wordcount: '186'
ht-degree: 100%

---

# 其他 Experience Cloud 解決方案的常見問題集{#faqs-for-other-experience-cloud-solutions}

關於搭配 ID 服務使用其他 Experience Cloud 解決方案的功能、功用和問題之常見問題集。

## Dynamic Tag Management (DTM) {#section-7ac4b9c1f1fd45a5a03eac3fb5968af7}

**我是否可使用「Dynamic Tag Management」來部署訪客 ID 服務?**

是，這是首選和建議的部署選項。

請參閱 [透過 DTM 實現的標準實作](../implementation-guides/standard.md#concept-89cd0199a9634fc48644f2d61e3d2445)。

## Analytics 與 Audience Manager {#section-b3dd206d497041acb04554c6fb1c912a}

**在我實作 Experience Cloud Identity 服務後，用戶的瀏覽歷史記錄會從 [!DNL Adobe Analytics] 匯出到 [!DNL Audience Manager] 嗎?**

您有兩個選擇:

* 如果在 ID 服務實作之後，用戶有任何瀏覽活動，用戶和其歷史記錄會包含在匯出至 [!DNL Audience Manager] 的資料中。
* 如果用戶在實作 ID 服務後沒有任何造訪活動，該訪客及其記錄將不會納入匯出到 Audience Manager 的資料中。因為沒有新活動，所以我們無法將 Analytics ID 與 Experience Cloud ID 建立關聯。
