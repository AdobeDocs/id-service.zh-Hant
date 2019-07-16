---
description: Experience Platform Identity Service在Adobe Experience Cloud中的角色。
keywords: ID 服務
seo-description: Experience Platform Identity Service在Adobe Experience Cloud中的角色。
seo-title: 關於 ID 服務
title: 概述
uuid: c52d6155-00a0-4fc5-9d8e-5ce00b8d01e6
translation-type: tm+mt
source-git-commit: 484c52265d8e0b6f0e79cb21d09082fff730a44b

---


# 關於 ID 服務{#aboutidservice}

Experience Platform Identity Service在Adobe Experience Cloud中的角色。

<!--
mcvid-functionality.xml
-->

## The Experience Platform Identity Service: A Foundational Element of Core Services {#section-2de0eb1d65664e92a4d8bbb167b84bde}

Experience Platform Identity Service可為Experience Cloud核心服務、解決方案以及People核心服務中的客戶屬性和受眾啓用通用識別架構。其運用方式為指派一個唯一的永久性 ID 給網站訪客。當您的組織實作 ID 服務時，此 ID 可讓您在不同的 Experience Cloud 解決方案中識別相同的網站訪客及其資料。

![](assets/ecid.png)

此外，ID 服務也能取代不同的解決方案專屬 ID (例如 Analytics AID)。而透過[客戶 ID 和驗證狀態](../reference/authenticated-state.md)功能，ID 服務可讓您將您的客戶 ID 傳遞至 [!DNL Experience Cloud]。但是請切記，ID 服務只能搭配您已訂閱的解決方案使用。如果您未註冊其他產品，便無法存取。

展望未來，ID 服務將成為許多目前與未來 [!DNL Experience Cloud] 特色、增強功能與服務的必要元件。目前 ID 服務支援 [Analytics](http://www.adobe.com/marketing-cloud/web-analytics.html)、[Audience Manager](http://www.adobe.com/marketing-cloud/data-management-platform.html) 和 [Target](http://www.adobe.com/marketing-cloud/testing-targeting.html)。此外，如果您想參與 [!DNL Adobe Experience Cloud] Device Co-op，也需要用到 ID 服務。如果您尚未實作 ID 服務，現在就是開始考慮移轉策略的最佳時機。For more information about the importance and role of the ID service, see [Why the Experience Platform Identity Service Should be on Your Radar](http://blogs.adobe.com/digitalmarketing/analytics/why-new-adobe-marketing-cloud-id-service-should-be-on-your-radar/).

## 功能摘要 {#section-96555473455c4bf8924c2d56ff4f3255}

總而言之，ID 服務可以:

* 建立通用機碼或 ID 以用於連結設定檔和身分識別。
* 在多個解決方案中辨識唯一裝置。
* 在客戶網域中設定第一方 Cookie 以確保可在相同網域進行追蹤。請參閱 [Experience Cloud](../introduction/cookies.md)。
* 從 [!DNL Experience Cloud] 客戶和合作夥伴接收別名和 ID 對應。
* 在 [!DNL Experience Cloud] 中管理 ID 同步。
* 在各廣告技術生態系統中，支援不同第三方的 ID 同步。
