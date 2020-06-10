---
title: 識別不重複訪客
description: Adobe ECID (ID 服務) 說明文件
translation-type: ht
source-git-commit: 8ad5ae179540596913fccc59070aecc57b09f586
workflow-type: ht
source-wordcount: '234'
ht-degree: 100%

---


# 識別不重複訪客

用於識別多筆內容中不重複訪客的方法包括，確定優先順序以確保該決定的準確性。下表顯示此優先順序：

| 使用的順序 | 查詢參數 (收集方法) | post_visid_type 欄值 | 顯示時機 |
|---|---|---|---|
|  1  | vid [s.visitorID](https://docs.adobe.com/content/help/zh-Hant/analytics/technotes/visitor-identification.html) | 0  | 已設定 `s.visitorID`。 |
|  2  | aid [s_vi cookie](https://docs.adobe.com/content/help/zh-Hant/analytics/technotes/visitor-identification.html) | 3  | 在您部署訪客 ID 服務之前，訪客已有 s_vi Cookie，或是您有設定訪客 ID 的[寬限期](https://docs.adobe.com/content/help/zh-Hant/id-service/using/reference/analytics-reference/grace-period.html)。 |
|  3  | mid [Identity Service 設定的 AMCV_ cookie](https://docs.adobe.com/content/help/zh-Hant/id-service/using/home.html) |  5  |  訪客的瀏覽器接受 Cookie (第一方)，且已部署 [!UICONTROL Identity Service]。 |
|  4  | fid [H.25.3 或更新版本的後援 Cookie，或 JavaScript 適用的 AppMeasurement](https://docs.adobe.com/content/help/zh-Hant/analytics/technotes/visitor-identification.html) |  4  | 訪客的瀏覽器接受 Cookie (第一方)。  |
|  5  |  [HTTP 行動訂閱者標題](https://docs.adobe.com/content/help/zh-Hant/analytics/technotes/visitor-identification.html)  |  2  | 系統將裝置識別為行動裝置。  |
|  6  | [IP 位址、使用者代理、閘道 IP 位址](https://docs.adobe.com/content/help/zh-Hant/analytics/technotes/visitor-identification.html) |  1  | 訪客的瀏覽器不接受 Cookie。 |

如需了解報告不重複訪客的方式，請參閱 [Analytics 中的不重複訪客](https://docs.adobe.com/content/help/zh-Hant/analytics/components/variables/dimensions-reports/reports-unique-visitors-v15-dsc.html)。
