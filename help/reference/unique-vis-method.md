---
title: 識別獨特訪客
description: Adobe ECID（ID服務）的檔案
translation-type: tm+mt
source-git-commit: 453a14a4b725dd14f445b089d083a83a5d2ffaa4

---


# 識別獨特訪客

用於識別多個上下文中的獨特訪客的方法包括確定優先順序順序以確保該確定的準確性。 下表顯示此優先順序：


 
|使用的訂單|查詢參數（收集方法）| post_visid_type欄值|在||—|—|—|—|| 1 |[vid(s.visitorID)](https://marketing.adobe.com/resources/help/en_US/sc/implement/visid_custom.html)| 0 | s.visitorID已設定。| 
| 2 | [aid (s_vi cookie)](https://marketing.adobe.com/resources/help/en_US/sc/implement/visid_analytics.html) | 3 |Visitor had an existing s_vi cookie before you deployed the Visitor ID service, or you have a Visitor ID [grace period](https://marketing.adobe.com/resources/help/en_US/mcvid/mcvid_grace_period.html) configured. || 3 |[mid（由Identity Service設定的AMCV_ cookie）](https://marketing.adobe.com/resources/help/en_US/mcvid/)| 5 |訪客的瀏覽器接受Cookie（第一方），且已部署Identity Service。 || 4 |[fid（H.25.3或更新版本的備援Cookie，或JavaScript適用的AppMeasurement）](https://marketing.adobe.com/resources/help/en_US/sc/implement/visid_fallback.html)| 4 |訪客的瀏覽器接受Cookie（第一方）。 || 5 |[HTTP行動訂閱者標題](https://marketing.adobe.com/resources/help/en_US/sc/implement/visid_mobile.html)| 2 |裝置可辨識為行動裝置。 || 6 |[IP位址、使用者代理、閘道IP位址](https://marketing.adobe.com/resources/help/en_US/sc/implement/visid_fallback.html)| 1 |訪客的瀏覽器不接受Cookie。 |


如需報告獨特訪客的詳細資訊，請參閱「Analytics中 [的獨特訪客」](https://docs.adobe.com/content/help/en/analytics/components/variables/dimensions-reports/reports-unique-visitors-v15-dsc.html)。
