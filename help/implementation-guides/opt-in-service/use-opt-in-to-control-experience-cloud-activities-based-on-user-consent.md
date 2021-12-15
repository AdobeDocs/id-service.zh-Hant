---
title: 根據用戶同意使用選擇加入以控制 Experience Cloud 活動
description: Adobe選擇加入物件是Adobe Experience Platform Identity Service的擴充功能，旨在協助您根據一般使用者同意，控制哪些Experience Cloud解決方案能否在網頁上建立Cookie及啟動指標。
exl-id: ac44e628-01ca-401c-864b-30fed0450e5f
source-git-commit: 0dca594c090095a01dfa2d02a98dfeba7ca02dca
workflow-type: tm+mt
source-wordcount: '526'
ht-degree: 47%

---

# 根據用戶同意控制 Experience Cloud 活動

Adobe [!UICONTROL 選擇加入] 物件是Adobe的擴充功能 [!UICONTROL Experience PlatformIdentity Service]，旨在協助您根據一般使用者同意，控制哪些Experience Cloud解決方案是否可在網頁上建立cookie或啟動指標。

## [!UICONTROL 選擇加入]的基本知識

隱私權法規的一個重要面向是取得並傳達用戶同意透過哪種方式及供哪些人使用其個人資料。最新版本 [!UICONTROL Identity服務] 包含的功能可根據使用者是否同意，有條件觸發（例如事前和事後同意）Experience Cloud解決方案標籤。 此程式如下圖所示：

![[!UICONTROL 選擇加入]的運作方式圖](assets/opt-in.png)

[!UICONTROL 選擇加入] 如下所示：

**如果在 Identity Service 中啟用[!UICONTROL 選擇加入] (透過布林值變數)，會延遲 Experience Cloud 解決方案程式庫觸發標籤或設定 Cookie，直到取得該解決方案的同意為止。**

[!UICONTROL 選擇加入] 也可讓您決定標籤是否在使用者同意前引發，然後儲存此同意資訊（連同一般使用者提供的同意），以便用於後續的點擊。 [!UICONTROL 選擇加入]選項中可儲存同意，或者您可以整合 CMP，使其儲存同意選取項目。

## 啟用和設定[!UICONTROL 選擇加入]

[!UICONTROL 選擇加入] 最輕鬆可使用Adobe Experience Platform標籤（先前稱為Launch）設定。 觀看以下短片，瞭解設定方式。

>[!VIDEO](https://video.tv.adobe.com/v/26431/?quality=12)

如果您未使用Experience Platform標籤，可以設定 [!UICONTROL 選擇加入]初始化全域訪客物件時的設定，如 [檔案](https://experienceleague.adobe.com/docs/id-service/using/implementation/opt-in-service/getting-started.html?lang=en).

## 在頁面上實作[!UICONTROL 選擇加入]

所有設定和後端內容都只是在準備向網站訪客顯示同意選項的介面。您可以自行建立此 UI，也可以透過 CMP (同意管理平台) 合作夥伴建立 UI。

設定使用[!UICONTROL 選擇加入]收集同意的 UI 時，應將其設定為呼叫與[!UICONTROL 選擇加入]連結的 API，並通知其同意部分或所有 Adobe Experience Cloud 解決方案。如需關於這些 API 的詳細資訊，請參閱[選擇加入參考文件](https://experienceleague.adobe.com/docs/id-service/using/implementation/opt-in-service/api.html?lang=en)。選擇加入的其他資訊也在相關文件頁面中。

## [!UICONTROL 選擇加入]示範

在以下影片中，請觀看的快速示範 [!UICONTROL 選擇加入] 操作頁面，以及如何影響Experience Cloud解決方案是否可設定cookie、啟動信標等。

>[!VIDEO](https://video.tv.adobe.com/v/26432/?quality=12)

**注意：** 必須指出，在編寫本條時， [!UICONTROL 選擇加入] 尚未內建至所有Experience Cloud應用程式的程式庫。 目前支援[!UICONTROL 選擇加入]的程式庫：

* Identity Service
* Analytics
* Audience Manager
* [!DNL Target]
