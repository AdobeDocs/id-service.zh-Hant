---
title: 識別不重複訪客
description: Adobe ECID (ID 服務) 說明文件
exl-id: 379dbf0a-814d-4348-9ac4-d0e8fc13b9dc
TQID: https://experienceleague.adobe.com/1iZMkBA6-SnhhVmqp8qrFuk-Ev-tKOae5FAduivghXM
product_v2:
  - id: e1971122-7081-4556-9222-8a31bd71800c
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: f8a45b24-4be7-4f1b-909b-60d06b483a20
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
  - id: c2be0313-b3ae-45e0-b454-d20bf54b23f2
  - id: eddd9b14-83bd-4ff4-9072-54a4a484abb7
source-git-commit: 5c41e39a833b527a329f62e5f0929445f47139de
workflow-type: tm+mt
source-wordcount: 251
ht-degree: 100%

---

# 識別不重複訪客

用於識別多筆內容中不重複訪客的方法包括，確定優先順序以確保該決定的準確性。 下表顯示此優先順序：

| 使用的順序 | 查詢參數 (收集方法) | post_visid_type 欄值 | 顯示時機 |
|---|---|---|---|
|  1  | vid [s.visitorID](https://experienceleague.adobe.com/docs/analytics/implementation/vars/config-vars/visitorid.html?lang=zh-Hant)  | 0  | 已設定 `s.visitorID`。 |
|  2  | aid [s_vi cookie](https://experienceleague.adobe.com/docs/core-services/interface/administration/ec-cookies/cookies-analytics.html?lang=zh-Hant#section-5d50a078de444d12b7d927d68ff3b679)  | 3  | 在您部署訪客 ID 服務之前，訪客已有 s_vi Cookie，或是您有設定訪客 ID 的[寬限期](https://experienceleague.adobe.com/docs/id-service/using/reference/analytics-reference/grace-period.html?lang=zh-Hant)。  |
|  3  | mid [身分識別服務設定的 AMCV_ cookie](../introduction/cookies.md)  |  5  |  訪客的瀏覽器接受 Cookie (第一方)，且已部署 [!DNL Identity Service]。  |
|  4  | fid [H.25.3 或更新版本的後援 Cookie，或 JavaScript 適用的 AppMeasurement](https://experienceleague.adobe.com/docs/core-services/interface/administration/ec-cookies/cookies-analytics.html?lang=zh-Hant#section-65e33f9bfc264959ac1513e2f4b10ac7)  |  4  |  訪客的瀏覽器接受 Cookie (第一方)。  |
|  5  |  [HTTP 行動訂閱者標題](https://experienceleague.adobe.com/docs/analytics/export/analytics-data-feed/data-feed-contents/datafeeds-reference.html?lang=zh-Hant)  |  2  |  系統將裝置識別為行動裝置。  |
|  6  |  [IP 位址、用戶代理程式、閘道 IP 位址](https://experienceleague.adobe.com/docs/analytics/components/metrics/unique-visitors.html?lang=zh-Hant)  |  1  |  訪客的瀏覽器不接受 Cookie。 |

{style="table-layout:auto"}

如需了解報告不重複訪客的方式，請參閱 [Analytics 中的不重複訪客](https://experienceleague.adobe.com/docs/analytics/components/metrics/unique-visitors.html?lang=zh-Hant)。

