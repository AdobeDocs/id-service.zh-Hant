---
title: 識別不重複訪客
description: Adobe ECID (ID 服務) 說明文件
translation-type: tm+mt
source-git-commit: d39cb79bac3a0a277e6390a8127c1f1b68579fa6
workflow-type: tm+mt
source-wordcount: '234'
ht-degree: 56%

---


# 識別不重複訪客

用於識別多筆內容中不重複訪客的方法包括，確定優先順序以確保該決定的準確性。下表顯示此優先順序：

| 使用的訂單 | 查詢參數（收集方法） | post_visid_type欄值 | 在 |
|---|---|---|---|
|  1  | vid [(s.visitorID)](https://docs.adobe.com/content/help/zh-Hant/analytics/technotes/visitor-identification.html)  | 0  | `s.visitorID` 的雙曲餘切值。 |
|  2  | aid  [(s_vi cookie)](https://docs.adobe.com/content/help/zh-Hant/analytics/technotes/visitor-identification.html)  | 3  | Visitor had an existing s_vi cookie before you deployed the Visitor ID service, or you have a Visitor ID [grace period](https://docs.adobe.com/content/help/zh-Hant/id-service/using/reference/analytics-reference/grace-period.html) configured.  |
|  3  | mid[（由Identity Service設定的AMCV_ Cookie）](https://docs.adobe.com/content/help/zh-Hant/id-service/using/home.html)  |  5  |  訪客的瀏覽器接受Cookie（第一方），且已部[!UICONTROL 署Identity Service]。  |
|  4  | fid [(fallback cookie on H.25.3 or newer, or AppMeasurement for JavaScript)](https://docs.adobe.com/content/help/zh-Hant/analytics/technotes/visitor-identification.html)  |  4  |  訪客的瀏覽器接受Cookie（第一方）。  |
|  5  |  [HTTP行動訂閱者標題](https://docs.adobe.com/content/help/zh-Hant/analytics/technotes/visitor-identification.html)  |  2  |  裝置可辨識為行動裝置。  |
|  6  |  [IP Address, User Agent, Gateway IP Address](https://docs.adobe.com/content/help/zh-Hant/analytics/technotes/visitor-identification.html)  |  1  |  訪客的瀏覽器不接受Cookie。 |

如需了解報告不重複訪客的方式，請參閱 Analytics 中的[不重複訪客](https://docs.adobe.com/content/help/zh-Hant/analytics/components/variables/dimensions-reports/reports-unique-visitors-v15-dsc.html)。
