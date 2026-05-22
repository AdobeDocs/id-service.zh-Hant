---
description: Experience Cloud 身分識別服務在 Adobe Experience Cloud 中的角色。
title: Experience Cloud 身分識別服務概觀
exl-id: dc7d6220-d42b-4a3e-bf37-1e4e87280ae1
TQID: https://experienceleague.adobe.com/fkT81V3iLEz2irg-3SDoyx733RNhqa2zWV1FgiXoYO4
product_v2: id: e1971122-7081-4556-9222-8a31bd71800c
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554id: c66ffd68-0f65-42bb-aa23-b4020f12e0bdid: f8a45b24-4be7-4f1b-909b-60d06b483a20id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
source-git-commit: 5c41e39a833b527a329f62e5f0929445f47139de
workflow-type: tm+mt
source-wordcount: 505
ht-degree: 100%

---

# Experience Cloud 身分識別服務概觀

Experience Cloud 身分識別服務可為 Experience Cloud 應用程式服務啟用共同識別架構。 您可以使用 Experience Cloud 身分識別服務設定 [Experience Cloud ID (ECID)](https://experienceleague.adobe.com/docs/experience-platform/identity/ecid.html)。

ECID 是跨 Adobe Experience Platform 和 Experience Cloud 應用程式使用的共用身分識別命名空間，用於追蹤訪客行為並確保每個裝置都有一個唯一身分識別碼，可跨多個工作階段持續存在。

>[!TIP]
>
>Experience Cloud 身分識別服務、Experience Platform 身分識別服務和 ECID 是三個&#x200B;**不同**&#x200B;實體。

Experience Cloud 身分識別服務可以取代不同的應用程式專用 ID，並使用[客戶 ID 和驗證狀態](/help/reference/authenticated-state.md)功能讓您將自己的客戶 ID 傳遞到 Experience Cloud。

>[!NOTE]
>
>Experience Cloud 身分識別服務僅適用於您訂閱的 Experience Cloud 應用程式服務，如果您未訂閱其他應用程式服務，則不會提供其存取權。

Experience Cloud 身分識別服務支援以下應用程式：

* [Adobe Analytics](https://business.adobe.com/products/analytics/web-analytics.html)
* [Audience Manager](https://business.adobe.com/products/audience-manager/adobe-audience-manager.html)
* [Adobe Target](https://business.adobe.com/products/target/adobe-target.html)

展望未來，ID 服務將成為許多目前與未來 Experience Cloud 功能、增強功能與服務的必要元件。 目前 ID 服務支援 [Analytics](http://www.adobe.com/tw/marketing-cloud/web-analytics.html)、[Audience Manager](http://www.adobe.com/tw/marketing-cloud/data-management-platform.html) 和 [Target](http://www.adobe.com/tw/marketing-cloud/testing-targeting.html)。 如果您尚未實作 ID 服務，現在就是開始考慮移轉策略的最佳時機。

## 功能摘要

總而言之，Experience Cloud 身分識別服務有助於：

* 跨多個應用程式唯一地識別裝置上的訪客。
* 設定客戶網域中的第一方 Cookie，以確保在相同的網域上追蹤。 如需詳細資訊，請參閱 [Cookie 和 Experience Cloud 身分識別服務](./cookies.md)的相關文件。
* 從 Experience Cloud 客戶和合作夥伴接收別名和 ID 對應。
* 在 Experience Cloud 中管理 ID 同步。
* 在各廣告技術生態系統中，支援不同第三方的 ID 同步。

## Experience Cloud 身分識別服務需求

您的解決方案和其他 Adobe 程式碼程式庫必須符合[某些要求](/help/reference/requirements.md)，您才可以使用身分識別服務。

* [Cookie 與 Experience Cloud 身分識別服務](cookies.md)：Experience Cloud 身分識別服務使用您的組織 ID、Experience Cloud AMCV Cookie 及 Demdex Cookie，為您的網站訪客建立並儲存不重複的永久識別碼。 這些 Cookie 可以讓 Experience Cloud 身分識別服務追蹤您不同網域上的訪客，並且讓您在不同的 Experience Cloud 解決方案間共用資料。
* [Experience Cloud 身分識別服務如何要求與設定 ID](id-request.md)：ID 要求與回應程序的概觀。 這些範例涵蓋在個別網站、跨不同網站，以及針對由不同 Experience Cloud 客戶 (具有自己的組織 ID) 管理的網站，進行 ID 指派。
* [了解 ID 同步和匹配率](match-rates.md)：概觀 Experience Cloud 身分識別服務 (包括 Adobe Media Optimizer 和身分識別服務) 中的 ID 同步程序與匹配率。

