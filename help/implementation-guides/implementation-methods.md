---
description: Experience Cloud Identity Service 的標準與非標準實作方法。
keywords: ID 服務
title: 實作方法
exl-id: 0fe40a3c-bdcd-4290-bcd7-25344ff108d6
source-git-commit: fa2549090e6790763a7ac6b87348789678d18ab6
workflow-type: tm+mt
source-wordcount: '136'
ht-degree: 100%

---

# 實作方法

您可以選擇使用 [!DNL Experience Cloud ID Service] 的標準 [!DNL Experience Platform Launch] 實作方法，或非標準實作方法。

>[!IMPORTANT]
>
>開始這些程序之前，請務必閱讀並了解 [ID 服務規定](../reference/requirements.md)。

## 標準實作 {#section-ea1e5270f2184f85a2e85214a6ac60cb}

Adobe 強烈建議使用 [[!DNL Experience Platform tags] 來實作 ID 服務。](https://experienceleague.adobe.com/docs/experience-platform/tags/home.html?lang=zh-Hant)此方法可確保整合其他 [!DNL Experience Cloud] 解決方案、簡化實作工作流程，並自動確認程式碼的位置和順序正確無誤。

## 非標準實作 {#section-2c4f2db1f9704315a7cccab6d2e07113}

本指南中的程序和程式碼範例可協助您以手動 (即非標準方法) 設定 [!DNL Experience Cloud] ID 服務。請注意，這些實作通常在技術上較複雜並具有挑戰性。您可能需要稀有的工程師人力，或必須用掉 Adobe 顧問合約支援時間。
