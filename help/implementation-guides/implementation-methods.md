---
description: Experience Cloud Identity service的標準與非標準實作方法。
keywords: ID 服務
seo-description: Experience Cloud Identity service的標準與非標準實作方法。
seo-title: 實作方式
title: 實作方式
uuid: d41250e2-09f4-4a8b-8ade-54d43e9281c9
translation-type: tm+mt
source-git-commit: e75a448a2fa1c384c88f00648a6f868a886c6569

---


# 實作方式

您可以使用、 [!DNL Experience Cloud ID Service] (DTM)或非 [!DNL Experience Platform Launch]標準方法 [!DNL Dynamic Tag Manager] 來選擇標準實作方法。

>[!IMPORTANT]
>
>開始進行這些程序之前，請務必閱讀並瞭解 [ID 服務需求](../reference/requirements.md)。

## 標準實作 {#section-ea1e5270f2184f85a2e85214a6ac60cb}

Adobe強烈建議使 [!DNL Experience Platform Launch](https://docs.adobe.com/content/help/en/launch/using/implement/solutions/idservice-save.html) 用來實作ID服務。 此方法可確保與其他解決方 [!DNL Experience Cloud] 案整合、簡化實施工作流程，並自動確保正確的程式碼放置和順序。

## 非標準實作 {#section-2c4f2db1f9704315a7cccab6d2e07113}

The procedures and code samples in this guide can help you set up the [!DNL Experience Cloud] ID service in a manual, or non-standard manner. 請注意，這些實作通常在技術上較複雜並具有挑戰性。您可能需要準備一些稀有的工程資源或必須用掉大量的 Adobe 顧問合約支援時間。

>[!TIP]
>
>另外，您也可以使用實作ID服務 [!DNL Dynamic Tag Manager](https://docs.adobe.com/content/help/en/dtm/using/dtm-home.html)。 不過，新客戶應該使用 [!DNL Experience Platform Launch]。 若要從升級 [!DNL Experience Platform Launch] 至 [!DNL Dynamic Tag Manager]，請 [參閱從DTM升級至Launch](https://docs.adobe.com/content/help/en/launch/using/reference/upgrade/overview.html))。
