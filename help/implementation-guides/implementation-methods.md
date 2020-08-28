---
description: Experience Cloud Identity Service 的標準與非標準實作方法。
keywords: ID Service
seo-description: Experience Cloud Identity Service 的標準與非標準實作方法。
seo-title: 實作方法
title: 實作方法
uuid: d41250e2-09f4-4a8b-8ade-54d43e9281c9
translation-type: ht
source-git-commit: 63de22a29ebd8a504800d1045a69ea7eec05077a
workflow-type: ht
source-wordcount: '153'
ht-degree: 100%

---


# 實作方法

您可以選擇使用 [!DNL Experience Cloud ID Service] 的標準 [!DNL Experience Platform Launch] 實作方法，或非標準實作方法。

>[!IMPORTANT]
>
>開始進行這些程序之前，請務必閱讀並瞭解 [ID 服務需求](../reference/requirements.md)。

## 標準實作 {#section-ea1e5270f2184f85a2e85214a6ac60cb}

Adobe 強烈建議使用 [[!DNL Experience Platform Launch]](https://docs.adobe.com/content/help/zh-Hant/launch/using/implement/solutions/idservice-save.translate.html) 實作 ID 服務。此方法可確保整合其他 [!DNL Experience Cloud] 解決方案、簡化實作工作流程，並自動確認程式碼的位置和順序正確無誤。

## 非標準實作 {#section-2c4f2db1f9704315a7cccab6d2e07113}

本指南中的程序和程式碼範例可協助您以手動 (即非標準方法) 設定 [!DNL Experience Cloud] ID 服務。請注意，這些實作通常在技術上較複雜並具有挑戰性。您可能需要稀有的工程師人力，或必須用掉 Adobe 顧問合約支援時間。
