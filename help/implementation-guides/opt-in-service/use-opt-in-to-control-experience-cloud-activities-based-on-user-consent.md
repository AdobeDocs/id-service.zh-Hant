---
title: 根據用戶同意使用選擇加入以控制 Experience Cloud 活動
description: Adobe 選擇加入物件是 Adobe Experience Platform 身分識別服務的擴充功能，旨在協助您根據一般用戶同意，控制哪些 Experience Cloud 解決方案能否在網頁上建立 Cookie 及啟動指標。
exl-id: ac44e628-01ca-401c-864b-30fed0450e5f
TQID: https://experienceleague.adobe.com/YfYkXzK8wKw6JC3-EB2ljIOfXGXQV5r6Nw2-XYsGW6c
product_v2:
  - id: e1971122-7081-4556-9222-8a31bd71800c
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: f8a45b24-4be7-4f1b-909b-60d06b483a20
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
  - id: f4e6943a-c91a-4134-a2c7-f4f20cfff2f0
source-git-commit: 5c41e39a833b527a329f62e5f0929445f47139de
workflow-type: tm+mt
source-wordcount: 517
ht-degree: 39%

---

# 根據用戶同意控制 Experience Cloud 活動

Adobe [!UICONTROL Opt-in]物件是Adobe [!UICONTROL Experience Platform Identity Service]的擴充功能，旨在協助您根據一般使用者同意，控制哪些Experience Cloud解決方案能否在網頁上建立Cookie及啟動指標。

## [!UICONTROL Opt-In]的基本知識

隱私權法規的一個重要面向是取得並傳達用戶同意透過哪種方式及供哪些人使用其個人資料。 最新版[!UICONTROL Identity Service]包含的功能會根據一般使用者是否同意，有條件觸發（例如事前和事後同意） Experience Cloud解決方案標籤。 此程序如下圖所示：

![&#x200B; [!UICONTROL Opt-in]運作方式圖表](assets/opt-in.png)

[!UICONTROL Opt-in]的運作方式如下：

**如果在Identity Service中啟用[!UICONTROL Opt-in] （透過布林值變數），會延遲Experience Cloud解決方案程式庫觸發標籤或設定Cookie，直到取得該解決方案的同意為止。**

[!UICONTROL Opt-in]也可讓您決定是否在使用者同意之前觸發標籤，然後儲存此同意資訊（連同一般使用者提供的同意），以便用於後續的點選。 [!UICONTROL Opt-in]選項中可儲存同意，或者您可以整合CMP，使其儲存同意選取專案。

## 正在啟用和設定[!UICONTROL Opt-In]

使用Adobe Experience Platform標籤（以前稱為Launch）可讓您以最輕鬆的方式設定[!UICONTROL Opt-in]。 觀看以下短片，瞭解設定方式。

>[!VIDEO](https://video.tv.adobe.com/v/26431/?quality=12)

如果您未使用Experience Platform標籤，可以在初始化全域Visitor物件時設定[!UICONTROL Opt-in]的設定，如[檔案](https://experienceleague.adobe.com/docs/id-service/using/implementation/opt-in-service/getting-started.html?lang=zh-Hant&lank=zh-Hant)所示。

## 在頁面上實作[!UICONTROL Opt-In]

所有設定和後端內容都只是在準備向網站訪客顯示同意選項的介面。 您可以自行建立此 UI，也可以透過 CMP (同意管理平台) 合作夥伴建立 UI。

設定UI以使用[!UICONTROL Opt-in]來收集同意時，應將其設定為呼叫與[!UICONTROL Opt-in]連結的API，並通知其同意部分或所有Adobe Experience Cloud解決方案。 如需關於這些 API 的詳細資訊，請參閱[選擇加入參考文件](https://experienceleague.adobe.com/docs/id-service/using/implementation/opt-in-service/api.html?lang=zh-Hant&lank=zh-Hant)。 選擇加入的其他資訊也在相關文件頁面中。

## [!UICONTROL Opt-In]個示範

在以下影片中，請觀看頁面上的[!UICONTROL Opt-in]快速示範，以及其如何影響Experience Cloud解決方案是否可設定Cookie、啟動指標等。

>[!VIDEO](https://video.tv.adobe.com/v/26432/?quality=12)

**注意：**&#x200B;請務必注意，撰寫本文時，[!UICONTROL Opt-in]尚未內建於所有Experience Cloud應用程式的程式庫。 目前支援[!UICONTROL Opt-in]的資料庫包括：

* 身分識別服務
* Analytics
* Audience Manager
* [!DNL Target]

