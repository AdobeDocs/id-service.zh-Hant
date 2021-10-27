---
description: 如果您有可在客戶造訪其他網域之前加以識別的主要進入網站，則 CNAME 將可讓您在不接受第三方 Cookie 的瀏覽器 (例如 Safari) 中使用跨網域追蹤功能。
keywords: 操作順序；ID 服務
title: CNAME 實施概觀
exl-id: f95dda3c-7bb2-4c7d-a25a-a4d20b58fe27
source-git-commit: 61f9f1888430ff0fdbb90a8cf6561bf23d204a45
workflow-type: tm+mt
source-wordcount: '266'
ht-degree: 45%

---

# CNAME 實施概觀{#cname-implementation-overview}

CNAME 實施可讓您自訂 Adobe 使用的收集網域，以符合您自己的網域。這些網域也稱為第一方收集網域。 這些實作可讓Adobe使用JavaScript在伺服器端設定第一方Cookie，而非在用戶端。 過去，伺服器端第一方 Cookie 不受 Apple 智慧追蹤預防 (ITP) 原則所限制。但是，在 2020 年 11 月，[!DNL Apple] 已更新其原則，因此相關限制也適用於透過 CNAME 設定的 Cookie。目前，透過CNAME在伺服器端設定的Cookie，以及透過Javascript在用戶端設定的Cookie，在ITP下都限制為七天或24小時到期。 如需 ITP 原則的詳細資訊，請參閱這篇關於[追蹤預防](https://webkit.org/tracking-prevention/#intelligent-tracking-prevention-itp)的 [!DNL Apple] 文件。

雖然CNAME實作在Cookie存留期方面並未提供任何好處，但可能會有其他好處。 這些優點包括廣告封鎖程式和不太常見的瀏覽器無法將資料傳送至分類為追蹤的網域。 在這些情況下，使用CNAME可防止使用這些工具的使用者中斷資料收集作業。

此外，CNAME實作可讓您指定 **[!UICONTROL 選擇自訂RDC類型]** 可控制使用者點擊最初路由的位置。 大部分的客戶不使用自訂RDC類型。
