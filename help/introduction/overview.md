---
description: Experience Cloud Identity Service 在 Adobe Experience Cloud 中的角色。
title: Experience CloudIdentity Service概述
exl-id: dc7d6220-d42b-4a3e-bf37-1e4e87280ae1
source-git-commit: f7c25f5ebd0690c56c081422949eb34f1f277ae1
workflow-type: tm+mt
source-wordcount: '489'
ht-degree: 36%

---

# Experience CloudIdentity Service概述

Experience Cloud身份服務為Experience Cloud應用服務啟用公共標識框架。 您可以使用Experience CloudIdentity服務來設定 [Experience CloudID(ECID)](https://experienceleague.adobe.com/docs/experience-platform/identity/ecid.html).

ECID是跨Adobe Experience Platform和Experience Cloud應用程式使用的共用身分命名空間，可追蹤訪客行為，並確保每個裝置都有可跨多個工作階段持續使用的唯一識別碼。

>[!TIP]
>
>Experience CloudIdentity Service、Experience PlatformIdentity Service和ECID為三個 **不同** 實體。

Experience CloudIdentity Service可取代不同的應用程式專屬ID，並使用 [客戶ID和驗證狀態](/help/reference/authenticated-state.md) 功能，讓您將自己的客戶ID傳遞至Experience Cloud。

>[!NOTE]
>
>Experience CloudIdentity服務只能與您所訂閱的Experience Cloud應用程式服務搭配使用，如果您未訂閱，將不提供對其他應用程式服務的存取。

Experience CloudIdentity服務支援以下應用程式：

* [Adobe Analytics](https://business.adobe.com/products/analytics/web-analytics.html)
* [Audience Manager](https://business.adobe.com/products/audience-manager/adobe-audience-manager.html)
* [Adobe Target](https://business.adobe.com/products/target/adobe-target.html)

展望未來，ID 服務將成為許多目前與未來 Experience Cloud 特色、增強功能與服務的必要元件。目前 ID 服務支援 [Analytics](http://www.adobe.com/tw/marketing-cloud/web-analytics.html)、[Audience Manager](http://www.adobe.com/tw/marketing-cloud/data-management-platform.html) 和 [Target](http://www.adobe.com/tw/marketing-cloud/testing-targeting.html)。如果您尚未實作 ID 服務，現在就是開始考慮移轉策略的最佳時機。

## 功能摘要

總之，Experience CloudIdentity服務可協助：

* 跨多個應用程式唯一識別裝置上的訪客。
* 設定客戶網域中的第一方 Cookie，以確保在相同的網域上追蹤。如需詳細資訊，請參閱 [Cookie 和 Experience Cloud Identity Service](./cookies.md) 的相關文件。
* 從 Experience Cloud 客戶和合作夥伴接收別名和 ID 對應。
* 在 Experience Cloud 中管理 ID 同步。
* 在各廣告技術生態系統中，支援不同第三方的 ID 同步。

## Experience CloudIdentity服務需求

您的解決方案和其他Adobe程式碼程式庫必須符合 [特定要求](/help/reference/requirements.md) 才能使用Identity Service。

* [Cookie與Experience CloudIdentity Service](cookies.md):Experience CloudIdentity Service Identity Service使用您的組織ID、Experience CloudAMCV Cookie及Demdex Cookie，為您的網站訪客建立並儲存不重複的永久識別碼。 這些Cookie可讓Identity Service追蹤您不同網域上的訪客，並啟用不同Experience Cloud解決方案之間的資料共用。
* [Experience Cloud Identity Service 如何要求與設定 ID](id-request.md)：ID 要求與回應程序的總覽。這些範例涵蓋在個別網站、跨不同網站，以及針對由不同 Experience Cloud 客戶 (具有自己的組織 ID) 管理的網站，進行 ID 指派。
* [了解ID同步和匹配率](match-rates.md):概述Experience CloudIdentity服務(包括Adobe Media Optimizer和Identity服務)中的ID同步程式與匹配率。
