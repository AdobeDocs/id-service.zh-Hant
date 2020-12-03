---
title: 根據使用者同意使用選擇加入以控制 Experience Cloud 活動
description: Adobe 選擇加入物件是 Adobe Experience Platform Identity Service 的擴充功能，旨在協助您根據一般使用者同意，控制哪些 Experience Cloud 解決方案能否在網頁上建立 Cookie 及啟動指標。
translation-type: tm+mt
source-git-commit: 3aba8820ef40d068c732a637be5ab67652a8d35d
workflow-type: tm+mt
source-wordcount: '554'
ht-degree: 100%

---


# 根據使用者同意控制 Experience Cloud 活動

Adobe [!UICONTROL 選擇加入]物件是 Adobe [!UICONTROL Experience Platform Identity Service] 的擴充功能，旨在協助您根據一般使用者同意，控制哪些 Experience Cloud 解決方案能否在網頁上建立 Cookie 及啟動指標。

## [!UICONTROL 選擇加入]的基本知識

隱私權法規的一個重要面向是取得並傳達使用者同意透過哪種方式及供哪些人使用其個人資料。最新版 [!UICONTROL Identity Service] 包含的功能介於使用者 (UI) 和 Adobe 解決方案之間，並根據一般使用者是否同意，有條件觸發 (例如事前和事後同意) Adobe Experience Cloud 解決方案標籤。這如下圖所示：

![[!UICONTROL 選擇加入]的運作方式圖](assets/opt-in.png)

[!UICONTROL 選擇加入]基本上是守門人… …或鑰匙管理員？由您決定。

歸根就底是：

**如果在 Identity Service 中啟用[!UICONTROL 選擇加入] (透過布林值變數)，會延遲 Experience Cloud 解決方案程式庫觸發標籤或設定 Cookie，直到取得該解決方案的同意為止。**

[!UICONTROL 選擇加入]也可讓您決定是否在使用者同意&#x200B;*之前*&#x200B;觸發任何標籤，然後儲存此同意資訊 (連同一般使用者提供的同意)，以便用於後續的點擊。[!UICONTROL 選擇加入]選項中可儲存同意，或者您可以整合 CMP，使其儲存同意選取項目。

## 啟用和設定[!UICONTROL 選擇加入]

此外，最輕鬆設定[!UICONTROL 選擇加入]的方法是透過 Adobe Experience Platform Launch。觀看以下短片，瞭解設定方式。

>[!VIDEO](https://video.tv.adobe.com/v/26431/?quality=12)

如果您沒有使用 Experience Platform Launch，可以在初始化全域「訪客」物件時指定[!UICONTROL 選擇加入]的設定，如[文件](https://marketing.adobe.com/resources/help/zh_TW/mcvid/getting-started.html)所示。

## 在頁面上實作[!UICONTROL 選擇加入]

所有設定和後端內容都只是在準備向網站訪客顯示同意選項的介面。您可以自行建立此 UI，也可以透過 CMP (同意管理平台) 合作夥伴建立 UI。

設定使用[!UICONTROL 選擇加入]收集同意的 UI 時，應將其設定為呼叫與[!UICONTROL 選擇加入]連結的 API，並通知其同意部分或所有 Adobe Experience Cloud 解決方案。如需關於這些 API 的詳細資訊，請參閱[選擇加入參考文件](https://marketing.adobe.com/resources/help/zh_TW/mcvid/api.html)。選擇加入的其他資訊也在相關文件頁面中。

## [!UICONTROL 選擇加入]示範

在以下影片中，請觀看頁面上的[!UICONTROL 選擇加入]快速示範，以及其如何影響 Experience Cloud 解決方案是否可設定 Cookie、啟動指標等。

>[!VIDEO](https://video.tv.adobe.com/v/26432/?quality=12)

**注意：**&#x200B;請務必注意，撰寫本文時，[!UICONTROL 選擇加入]尚未內建於所有 Experience Cloud 解決方案的程式庫。目前支援[!UICONTROL 選擇加入]的程式庫：

* Identity Service
* Analytics
* Audience Manager
* [!DNL Target]
