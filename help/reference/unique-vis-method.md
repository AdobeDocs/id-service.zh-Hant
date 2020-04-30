---
title: 識別不重複訪客
description: Adobe ECID (ID 服務) 說明文件
translation-type: tm+mt
source-git-commit: dee27fb0150ce2c40f570f98b9af0b6904c16814

---


# 識別不重複訪客

用於識別多筆內容中不重複訪客的方法包括，確定優先順序以確保該決定的準確性。下表顯示此優先順序: 
| 使用的順序 | 查詢參數 (集合方法) | post_visid_type 欄值 | 顯示時機 |
|--- |--- |--- |--- |
| 1 | [vid (s.visitorID)](https://marketing.adobe.com/resources/help/zh_TW/sc/implement/visid_custom.html) | 0 |s.visitorID 已設定。|
| 2 | [aid (s_vi cookie)](https://marketing.adobe.com/resources/help/zh_TW/sc/implement/visid_analytics.html) | 3 |Visitor had an existing s_vi cookie before you deployed the Visitor ID service, or you have a Visitor ID [grace period](https://marketing.adobe.com/resources/help/zh_TW/mcvid/mcvid_grace_period.html) configured. |
| 3 | [mid (身分識別服務設定的 AMCV_ cookie)](https://marketing.adobe.com/resources/help/zh_TW/mcvid/) | 5 | 訪客的瀏覽器接受 Cookie (第一方)，且已部署身分識別服務。 |
| 4 | [fid (H.25.3 或更新版本上的遞補 Cookie，或適用於 JavaScript 的 AppMeasurement)](https://marketing.adobe.com/resources/help/zh_TW/sc/implement/visid_fallback.html) | 4 | 訪客的瀏覽器接受 Cookie (第一方)。 |
| 5 | [HTTP 行動訂閱者標頭](https://marketing.adobe.com/resources/help/zh_TW/sc/implement/visid_mobile.html) | 2 | 裝置已辨識為行動裝置。 |
| 6 | [IP 位址、使用者代理程式、閘道 IP 位址](https://marketing.adobe.com/resources/help/zh_TW/sc/implement/visid_fallback.html) | 1 | 訪客的瀏覽器不接受 Cookie。 |

如需了解報告不重複訪客的方式，請參閱 Analytics 中的[不重複訪客](https://docs.adobe.com/content/help/zh-Hant/analytics/components/variables/dimensions-reports/reports-unique-visitors-v15-dsc.html)。
