---
description: 如果您有可在客戶造訪其他網域之前加以識別的主要進入網站，則 CNAME 將可讓您在不接受第三方 Cookie 的瀏覽器 (例如 Safari) 中使用跨網域追蹤功能。
keywords: 操作順序；ID 服務
title: CNAME 實施概觀
source-git-commit: 06e935a4ba4776baa900d3dc91e294c92b873c0f
workflow-type: tm+mt
source-wordcount: '221'
ht-degree: 100%

---


# CNAME 實施概觀{#cname-implementation-overview}

CNAME 實施可讓您自訂 Adobe 使用的收集網域，以符合您自己的網域。這可讓 Adobe 在伺服器端設定第一方 Cookie，而非使用 JavaScript 在用戶端設定。過去，伺服器端第一方 Cookie 不受 Apple 智慧追蹤預防 (ITP) 原則所限制。但是，在 2020 年 11 月，[!DNL Apple] 已更新其原則，因此相關限制也適用於透過 CNAME 設定的 Cookie。目前，透過 CNAME 在伺服器端設定的 Cookie 和透過 JavaScript 在用戶端設定的 Cookie，依據 ITP 原則都限制為 7 天或 24 小時到期。如需 ITP 原則的詳細資訊，請參閱這篇關於[追蹤預防](https://webkit.org/tracking-prevention/#intelligent-tracking-prevention-itp)的 [!DNL Apple] 文件。

雖然 CNAME 實施未提供 Cookie 存留期方面的任何好處，但可能還有其他一些好處，例如廣告封鎖程式和較不常見的瀏覽器防止將資料傳送至這些程式和瀏覽器分類為追蹤器的網域。在這些情況下，使用 CNAME 可防止這些工具使用者的資料收集中斷問題。