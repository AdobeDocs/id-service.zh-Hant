---
description: 訪客ID服務在Adobe CX Enterprise中的角色。
title: Adobe訪客ID服務總覽
exl-id: dc7d6220-d42b-4a3e-bf37-1e4e87280ae1
TQID: https://experienceleague.adobe.com/fkT81V3iLEz2irg-3SDoyx733RNhqa2zWV1FgiXoYO4
product_v2: id: e1971122-7081-4556-9222-8a31bd71800c
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554id: c66ffd68-0f65-42bb-aa23-b4020f12e0bdid: f8a45b24-4be7-4f1b-909b-60d06b483a20id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
source-git-commit: 09ee359440c122702a6ce83708c98af3862c9cc9
workflow-type: tm+mt
source-wordcount: 497
ht-degree: 18%

---

# Adobe訪客ID服務總覽

Adobe訪客ID服務可為CX Enterprise Application Services啟用共同識別架構。 您可以使用訪客ID服務來設定[ECID](https://experienceleague.adobe.com/docs/experience-platform/identity/ecid.html)。

ECID是跨Adobe Experience Platform和CX Enterprise應用程式使用的共用身分名稱空間，用來追蹤訪客行為並確保每個裝置都有可在多個工作階段儲存的唯一識別碼。

>[!TIP]
>
>訪客ID服務、Experience Platform Identity服務和ECID是三個&#x200B;**不同**&#x200B;實體。

訪客ID服務可以取代不同的應用程式專用ID，並使用[客戶ID和驗證狀態](/help/reference/authenticated-state.md)功能讓您將自己的客戶ID傳遞到CX Enterprise。

>[!NOTE]
>
>訪客ID服務僅適用於您訂閱的CX Enterprise Application Services，如果您未訂閱其他應用程式服務，則不會提供其存取權。

訪客ID服務支援下列應用程式：

* [Adobe Analytics](https://business.adobe.com/products/analytics/web-analytics.html)
* [Audience Manager](https://business.adobe.com/products/audience-manager/adobe-audience-manager.html)
* [Adobe Target](https://business.adobe.com/products/target/adobe-target.html)

展望未來，訪客ID服務將成為許多目前與未來CX Enterprise特色、增強功能與服務的必要元件。 目前，訪客ID服務支援[Analytics](http://www.adobe.com/tw/marketing-cloud/web-analytics.html)、[Audience Manager](http://www.adobe.com/tw/marketing-cloud/data-management-platform.html)和[Target](http://www.adobe.com/tw/marketing-cloud/testing-targeting.html)。 如果您尚未實作訪客ID服務，現在就是開始考慮移轉策略的最佳時機。

## 功能摘要

總而言之，訪客ID服務有助於：

* 跨多個應用程式唯一地識別裝置上的訪客。
* 設定客戶網域中的第一方 Cookie，以確保在相同的網域上追蹤。 如需詳細資訊，請參閱[Cookie和訪客ID服務](./cookies.md)的相關檔案。
* 從CX Enterprise客戶和合作夥伴接收別名和ID對應。
* 管理CX Enterprise內的ID同步。
* 在各廣告技術生態系統中，支援不同第三方的 ID 同步。

## 訪客ID服務需求

您的解決方案和其他Adobe程式碼程式庫必須符合[特定需求](/help/reference/requirements.md)，您才能使用訪客ID服務。

* [Cookie與訪客ID服務](cookies.md)：訪客ID服務會使用您的IMS組織ID、CX Enterprise AMCV Cookie及Demdex Cookie，為您的網站訪客建立並儲存唯一的永久性識別碼。 這些Cookie可讓訪客ID服務追蹤您不同網域的訪客，並啟用不同CX企業解決方案之間的資料共用。
* [訪客ID服務如何要求與設定ID](id-request.md)： ID要求與回應程式的總覽。 這些範例涵蓋在個別網站、跨不同網站，以及針對由不同CX Enterprise客戶（具有自己的IMS組織ID）管理的網站，進行ID指派。
* [瞭解ID同步和匹配率](match-rates.md)：概述訪客ID服務（包括Adobe Media Optimizer和訪客ID服務）中的ID同步程式與匹配率。

