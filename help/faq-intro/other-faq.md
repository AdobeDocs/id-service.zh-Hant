---
description: 關於搭配 ID 服務使用其他 Experience Cloud 解決方案的功能、功用和問題之常見問題集。
keywords: ID Service
seo-description: 關於搭配 ID 服務使用其他 Experience Cloud 解決方案的功能、功用和問題之常見問題集。
seo-title: 其他 Experience Cloud 解決方案的常見問題集
title: 其他 Experience Cloud 解決方案的常見問題集
uuid: 7d848663-6cbb-4d80-ab06-7b6d2dc20e2b
translation-type: tm+mt
source-git-commit: e6d65f1bfed187d7440512e8f3c2de0550506c95
workflow-type: tm+mt
source-wordcount: '209'
ht-degree: 68%

---


# 其他 Experience Cloud 解決方案的常見問題集{#faqs-for-other-experience-cloud-solutions}

關於搭配 ID 服務使用其他 Experience Cloud 解決方案的功能、功用和問題之常見問題集。

## Dynamic Tag Management (DTM) {#section-7ac4b9c1f1fd45a5a03eac3fb5968af7}

**我是否可使用「Dynamic Tag Management」來部署訪客 ID 服務?**

是的，這是首選和建議的部署選項。

See [Standard Implementation with DTM](../implementation-guides/standard.md#concept-89cd0199a9634fc48644f2d61e3d2445).

## Analytics 與 Audience Manager {#section-b3dd206d497041acb04554c6fb1c912a}

**在我實作 Experience Cloud Identity 服務後，使用者的瀏覽歷史記錄會從 [!DNL Adobe Analytics] 匯出到 [!DNL Audience Manager] 嗎?**

您有兩個選擇:

* 如果在 ID 服務實作之後，使用者有任何瀏覽活動，使用者和其歷史記錄會包含在匯出至 [!DNL Audience Manager] 的資料中。
* 如果使用者在實施ID服務後沒有任何造訪活動，則訪客及其歷史記錄不會包含在匯出至Audience Manager的資料中。 由於沒有新活動，因此我們無法將Analytics ID與Experience Cloud ID建立關聯。

