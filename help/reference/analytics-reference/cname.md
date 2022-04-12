---
description: 如果您有可在客戶造訪其他網域之前加以識別的主要進入網站，則 CNAME 將可讓您在不接受第三方 Cookie 的瀏覽器 (例如 Safari) 中使用跨網域追蹤功能。
keywords: 操作順序；ID 服務
title: CNAME 實施概觀
exl-id: f95dda3c-7bb2-4c7d-a25a-a4d20b58fe27
source-git-commit: d2586fc722be25df1b82caaf2cc6de6a2a6c31bf
workflow-type: tm+mt
source-wordcount: '275'
ht-degree: 92%

---

# CNAME 實施概觀{#cname-implementation-overview}

CNAME 實施可讓您自訂 Adobe 使用的集合網域，以符合您自己的網域。這些網域也稱為第一方集合網域。這些實施可讓 Adobe 在伺服器端上設定第一方 Cookie，而非使用 JavaScript 在用戶端上設定。過去，伺服器端第一方 Cookie 不受 Apple 智慧追蹤預防 (ITP) 原則所限制。但是，在 2020 年 11 月，[!DNL Apple] 已更新其原則，因此相關限制也適用於透過 CNAME 設定的 Cookie。目前，透過 CNAME 在伺服器端設定的 Cookie 和透過 JavaScript 在用戶端設定的 Cookie，依據 ITP 原則都限制為 7 天或 24 小時到期。如需 ITP 原則的詳細資訊，請參閱這篇關於[追蹤預防](https://webkit.org/tracking-prevention/#intelligent-tracking-prevention-itp)的 [!DNL Apple] 文件。

雖然 CNAME 實施無法在 Cookie 生命週期方面提供任何優勢，但它還是有一些其他的優點。這些優點包括廣告攔截程式和不太常見的瀏覽器，防止將資料傳送到遭其歸類為追蹤程式的網域。在這些情況下，使用 CNAME 可防止這些工具使用者的資料彙集中斷問題。

此外， CNAME實現允許您 [選擇自定義RDC類型](https://experienceleague.adobe.com/docs/analytics/technotes/rdc/regional-data-collection.html?lang=zh-Hant) 它控制用戶命中的初始路由位置。 大多數客戶不使用自訂 RDC 類型。
