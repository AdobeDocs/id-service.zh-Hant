---
description: Experience Cloud Identity 服務在 Adobe Experience Cloud 中的角色。
seo-description: Experience Cloud Identity 服務 (原稱為訪客 ID 服務或 Marketing Cloud ID 服務) 可啟用 Experience Cloud 服務的共同識別架構，例如客戶屬性和對象。
seo-title: Experience Cloud ID 服務概述
title: Experience Cloud ID 服務概述
exl-id: dc7d6220-d42b-4a3e-bf37-1e4e87280ae1
source-git-commit: b907ffcbfbb8851ce6279b614dc58c22f2ce9907
workflow-type: tm+mt
source-wordcount: '606'
ht-degree: 100%

---

# Experience Cloud ID 服務概述

[!UICONTROL Experience Cloud Identity 服務]可在 Experience Platform Identity 中啟用 Experience Cloud 核心服務 (例如客戶屬性和對象) 解決方案的共同識別架構。

>[!NOTE]
>
> 提及 ID 服務之處或許會使用簡稱或服務原本的名稱，例如 ECID、Marketing Cloud ID 服務 (MID) 和訪客 ID 服務。這些名稱指的都是 [!UICONTROL Experience Cloud Identity 服務]。您也可能看到 [!UICONTROL Experience Platform Identity 服務]的說法。事實釐清：

* [!UICONTROL Experience Platform Identity 服務]：連結身分識別的服務。這項裝置連結服務主要是依人員提供體驗管理功能。
* [!UICONTROL Experience Cloud ID 服務] (ECID)：為網站訪客指派能持續使用的不重複 ID。這個確切實體可供 Platform Identity 服務使用。

當您的組織實作 ID 服務時，此 ID 可讓您在不同的 Experience Cloud 解決方案中識別相同的網站訪客及其資料。

![](assets/ecid-new.png)

此外，ID 服務也可以取代不同的解決方案專屬 ID (例如 Analytics AID)。透過[客戶 ID 和驗證狀態](/help/reference/authenticated-state.md)功能，ID 服務可讓您將您的客戶 ID 傳遞至 Experience Cloud。但是請牢記一點，ID 服務僅適用於您已經訂閱的解決方案。它無法讓您存取您尚未註冊的其他產品。

展望未來，ID 服務將成為許多目前與未來 Experience Cloud 特色、增強功能與服務的必要元件。目前 ID 服務支援 [Analytics](http://www.adobe.com/tw/marketing-cloud/web-analytics.html)、[Audience Manager](http://www.adobe.com/tw/marketing-cloud/data-management-platform.html) 和 [Target](http://www.adobe.com/tw/marketing-cloud/testing-targeting.html)。此外，如果您想參與 Adobe Experience Cloud Device Co-op，也需要用到 ID 服務。如果您尚未實作 ID 服務，現在就是開始考慮移轉策略的最佳時機。如需 ID 服務之重要性和角色的詳細資訊，請參閱[為何您應認真考慮 Experience Cloud Identity 服務](http://blogs.adobe.com/digitalmarketing/analytics/why-new-adobe-marketing-cloud-id-service-should-be-on-your-radar/)。

## 功能摘要

總而言之，ID 服務可以：

* 建立可用來連結設定檔和身分識別的公用鍵或 ID。
* 可唯一識別多個解決方案中的裝置。
* 在客戶的網域中設定第一方 Cookie，以確保可在相同網域上追蹤。如需詳細資訊，請參閱 [Cookie 和 Experience Cloud Identity 服務](./cookies.md)的相關文件。
* 從 Experience Cloud 客戶和合作夥伴接收別名和 ID 對應。
* 在 Experience Cloud 中管理 ID 同步。
* 在各廣告技術生態系統中，支援不同第三方的 ID 同步。

## ID 服務要求

您的解決方案和其他 Adobe 程式碼程式庫必須符合[某些要求](/help/reference/requirements.md)，您才可以使用 ID 服務。

* [Cookie 與 Experience Cloud Identity 服務](cookies.md)：ID 服務使用您的組織 ID、Experience Cloud AMCV Cookie 及 Demdex Cookie，為您的網站訪客建立並儲存不重複的永久識別碼。這些 Cookie 可以讓 ID 服務追蹤您不同網域上的訪客，並且讓您在不同的 Experience Cloud 解決方案間共用資料。
* [Experience Cloud Identity 服務如何要求與設定 ID](id-request.md)：概述 ID 要求與回應程序。這些範例涵蓋在個別網站、跨不同網站，以及針對由不同 Experience Cloud 客戶 (具有自己的組織 ID) 管理的網站，進行 ID 指派。
* [了解 ID 同步和匹配率](match-rates.md)：概述 Experience Cloud Identity 服務 (包括 Adobe Media Optimizer 和 ID 服務) 中的 ID 同步程序與匹配率。
