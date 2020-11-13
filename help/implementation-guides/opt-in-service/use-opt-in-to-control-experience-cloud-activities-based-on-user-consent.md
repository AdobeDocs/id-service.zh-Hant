---
title: 根據使用者同意，使用選擇加入來控制Experience Cloud活動
description: Adobe Opt-in Object是Adobe Experience Platform Identity Service的擴充功能，旨在協助您根據使用者的同意，控制Experience Cloud解決方案是否可在網頁上建立Cookie，以及哪些Experience Cloud解決方案可以啟動信標。
translation-type: tm+mt
source-git-commit: 3aba8820ef40d068c732a637be5ab67652a8d35d
workflow-type: tm+mt
source-wordcount: '554'
ht-degree: 0%

---


# 根據使用者同意控制Experience Cloud活動

Adobe [!UICONTROL Opt-in] Object是Adobe Experience Platform Identity Service的擴充功能，旨在協助您根據使用者同意，控制Experience Cloud解決方案是否可在網頁上建立Cookie或啟動信標，以及哪些Experience Cloud解決方案可以。

## 選擇加 [!UICONTROL 入的基本概念]

隱私權法規的一個重要方面是取得並傳遞使用者同意書，告知使用者個人資料的使用方式及使用者。 最新版 [!UICONTROL Identity Service] （身分服務）包含的功能介於使用者(UI)和Adobe解決方案之間，並根據使用者是否同意，提供Adobe Experience Cloud解決方案標籤的條件性觸發（例如，事前和事後同意）。 這如下圖所示：

![選擇加入 [!UICONTROL 的運作方式]](assets/opt-in.png)

[!UICONTROL 選擇加入] ，基本上就是看門人……還是鑰匙手？ 由您決定。

歸根到底是：

**如果 [!UICONTROL 在Identity Service中啟用] （透過布林變數）選擇加入，會延遲Experience Cloud解決方案程式庫不觸發標籤或設定Cookie，直到取得該解決方案的同意為止。**

[!UICONTROL Opt-in]** 也可讓您決定是否在使用者同意前觸發任何標籤，然後會儲存此同意資訊（連同使用者給予的同意），以便用於後續的點擊。 「選擇加入」選項中提供 [!UICONTROL 許可的儲存] ，或者您可以與CMP整合併讓其儲存許可選擇。

## 啟用和設 [!UICONTROL 定選擇加入]

[!UICONTROL 使用Adobe Experience Platform Launch] ，您也可以最輕鬆地設定選擇加入。 檢視下列短片，瞭解其方式。

>[!VIDEO](https://video.tv.adobe.com/v/26431/?quality=12)

如果您不使用Experience Platform Launch，可以在全域訪客物件的初始化中設定 [!UICONTROL Opt-in]』s configuration，如說明檔案所 [示](https://marketing.adobe.com/resources/help/en_US/mcvid/getting-started.html)。

## 在頁 [!UICONTROL 面上實作] 選擇加入

所有這些設定和後端內容都只是為提供介面，讓網站訪客可使用同意選項來呈現。 此UI可由您建立，或者您可以使用CMP（許可管理平台）合作夥伴來建立UI。

設定使用 [!UICONTROL Opt-in] （選擇加入）收集同意的UI時，應將其設定為呼叫會與  Opt-in（選擇加入）連結的API，並通知其同意部分或所有Adobe Experience Cloud解決方案。 有關這些API的詳細資訊，請參閱 [加入參考檔案](https://marketing.adobe.com/resources/help/en_US/mcvid/api.html)。 其他有關選擇加入的資訊也在周圍的檔案頁面中。

## [!UICONTROL 選擇加入] 示範

在以下影片中，請參閱 [!UICONTROL Opt-in] working the page的快速示範，以及它如何影響Experience Cloud解決方案是否可設定Cookie、啟始信標等。

>[!VIDEO](https://video.tv.adobe.com/v/26432/?quality=12)

**注意：** 請務必注意，在撰寫本文時， [!UICONTROL Opt-in] 尚未內建到所有Experience Cloud解決方案的程式庫中。 目前支援選擇加入的 [!UICONTROL 程式庫] :

* Identity 服務
* Analytics
* Audience Manager
* [!DNL Target]
