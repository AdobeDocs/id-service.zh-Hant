---
description: Experience Cloud Identity服務在Adobe Experience cloud中的角色。
seo-description: Experience Cloud Identity Service（舊稱訪客ID服務或Marketing Cloud ID服務）可啟用Experience cloud服務的通用識別架構，例如客戶屬性和觀眾。
seo-title: Experience Cloud ID服務概觀
title: Experience Cloud ID服務概觀
translation-type: tm+mt
source-git-commit: 98b72f87b188debd6a5f6b86822c3f714647de61

---


# Experience Cloud ID服務概觀

The [!UICONTROL Experience Cloud Identity Service] enables the common identification framework for Experience Cloud Core Services (such as customer attributes and audiences) solutions in the Experience Platform Identity Service.

>[!NOTE]
>
> 您可能會將ID服務的參照視為縮略詞或先前的名稱，例如ECID、Marketing Cloud ID服務(MID)和訪客ID服務。 這些指的是 [!UICONTROL Experience Cloud Identity Service]。 您也可能會看 [!UICONTROL 到Experience Platform Identity Service]。 要澄清：

* [!UICONTROL Experience Platform Identity Service]:連結身分的服務。 它是提供人員型體驗管理的裝置連結服務。
* [!UICONTROL Experience Cloud ID服務] (ECID):指派給網站訪客的唯一、永續性ID。 它是平台身分服務可使用的特定實體。

當您的組織實作 ID 服務時，此 ID 可讓您在不同的 Experience Cloud 解決方案中識別相同的網站訪客及其資料。

![](assets/ecid-new.png)

此外，ID 服務也能取代不同的解決方案專屬 ID (例如 Analytics AID)。而透過[客戶 ID 和驗證狀態](/help/reference/authenticated-state.md)功能，ID 服務可讓您將您的客戶 ID 傳遞至 Experience Cloud。但是請切記，ID 服務只能搭配您已訂閱的解決方案使用。如果您未註冊其他產品，便無法存取。

展望未來，ID 服務將成為許多目前與未來 Experience Cloud 特色、增強功能與服務的必要元件。目前 ID 服務支援 [Analytics](http://www.adobe.com/marketing-cloud/web-analytics.html)、[Audience Manager](http://www.adobe.com/marketing-cloud/data-management-platform.html) 和 [Target](http://www.adobe.com/marketing-cloud/testing-targeting.html)。此外，如果您想參與 Adobe Experience Cloud Device Co-op，也需要用到 ID 服務。如果您尚未實作 ID 服務，現在就是開始考慮移轉策略的最佳時機。如需 ID 服務之重要性和角色的詳細資訊，請參閱[為何您應認真考慮 Experience Cloud Identity 服務](http://blogs.adobe.com/digitalmarketing/analytics/why-new-adobe-marketing-cloud-id-service-should-be-on-your-radar/)。

## 功能摘要

總而言之，ID 服務可以:

* 建立通用機碼或 ID 以用於連結設定檔和身分識別。
* 在多個解決方案中辨識唯一裝置。
* 在客戶網域中設定第一方 Cookie 以確保可在相同網域進行追蹤。請參閱 cookies和Experience Cloud [Identity Service上的檔案](https://docs.adobe.com/content/help/en/id-service/using/intro/cookies.html) ，以取得詳細資訊。
* 從 Experience Cloud 客戶和合作夥伴接收別名和 ID 對應。
* 在 Experience Cloud 中管理 ID 同步。
* 在各廣告技術生態系統中，支援不同第三方的 ID 同步。

## ID 服務需求

您的解決方案和其他 Adobe 程式碼程式庫必須符合[特定需求](/help/reference/requirements.md)，您才能使用 ID 服務。

* [Cookie 與 Experience Cloud Identity 服務](cookies.md): ID 服務使用您的組織 ID、Experience Cloud AMCV Cookie 及 Demdex Cookie，為您的網站訪客建立並儲存不重複的永久識別碼。這些 Cookie 可以讓 ID 服務追蹤您不同網域上的訪客，並且讓您在不同的 Experience Cloud 解決方案間共用資料。
* [Experience Cloud Identity 服務如何要求與設定 ID](id-request.md): 概述 ID 要求與回應程序。這些範例涵蓋在個別網站、跨不同網站，以及針對由不同 Experience Cloud 客戶 (具有自己的組織 ID) 管理的網站，進行 ID 指派。
* [瞭解 ID 同步和匹配率](match-rates.md): 概述 Experience Cloud Identity 服務 (包括 Adobe Media Optimizer 和 ID 服務) 中的 ID 同步程序與匹配率。
