---
description: Experience Cloud Identity Service 在 Adobe Experience Cloud 中的角色。
keywords: ID 服務
title: 總覽
exl-id: d907e299-bde0-4b5f-8c16-867a4eaa8be1
source-git-commit: 2c87022baeb09a8767d0d9627bf2b607c51b2503
workflow-type: tm+mt
source-wordcount: '310'
ht-degree: 100%

---

# 關於 ID 服務{#aboutidservice}

Experience Cloud Identity Service 在 Adobe Experience Cloud 中的角色。

<!--
mcvid-functionality.xml
-->

## Experience Cloud Identity Service：核心服務的基本要素 {#section-2de0eb1d65664e92a4d8bbb167b84bde}

Experience Cloud Identity Service 可為 Experience Cloud 核心服務、解決方案以及客戶屬性和觀眾啟用共同識別架構。其運用方式為指派一個唯一的永久性 ID 給網站訪客。當您的組織實作 ID 服務時，此 ID 可讓您在不同的 Experience Cloud 解決方案中識別相同的網站訪客及其資料。

![](assets/ecid-new.png)

此外，ID 服務也可以取代不同的解決方案專屬 ID (例如 Analytics AID)。此外，透過[客戶 ID 和驗證狀態](../reference/authenticated-state.md)功能，ID 服務可讓您將您的客戶 ID 傳遞至 [!DNL Experience Cloud]。但是請牢記一點，ID 服務僅適用於您已經訂閱的解決方案。它無法讓您存取您尚未註冊的其他產品。

展望未來，ID 服務將成為許多目前與未來 [!DNL Experience Cloud] 特色、增強功能與服務的必要元件。目前 ID 服務支援 [Analytics](http://www.adobe.com/tw/marketing-cloud/web-analytics.html)、[Audience Manager](http://www.adobe.com/tw/marketing-cloud/data-management-platform.html) 和 [Target](http://www.adobe.com/tw/marketing-cloud/testing-targeting.html)。此外，如果您想參與 [!DNL Adobe Experience Cloud] Device Co-op，也需要用到 ID 服務。 如果您尚未實作 ID 服務，現在就是開始考慮移轉策略的最佳時機。

## 功能摘要 {#section-96555473455c4bf8924c2d56ff4f3255}

總而言之，ID 服務可以：

* 建立可用來連結設定檔和身分識別的公用鍵或 ID。
* 可唯一識別多個解決方案中的裝置。
* 在客戶的網域中設定第一方 Cookie，以確保可在相同網域上追蹤。請參閱 [Experience Cloud](../introduction/cookies.md)。
* 從 [!DNL Experience Cloud] 客戶和合作夥伴接收別名和 ID 對應。
* 在 [!DNL Experience Cloud] 中管理 ID 同步。
* 在各廣告技術生態系統中，支援不同第三方的 ID 同步。
