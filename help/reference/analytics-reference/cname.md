---
description: 如果您有可在客戶造訪其他網域之前加以識別的主要進入網站，則 CNAME 將可讓您在不接受第三方 Cookie 的瀏覽器 (例如 Safari) 中使用跨網域追蹤功能。
keywords: 操作順序；ID 服務
seo-description: 如果您有可在客戶造訪其他網域之前加以識別的主要進入網站，則 CNAME 將可讓您在不接受第三方 Cookie 的瀏覽器 (例如 Safari) 中使用跨網域追蹤功能。
seo-title: CNAME實作概觀
title: CNAME實作概觀
uuid: ba42c822-b677-4139-b1ed-4d98d3320fd0
translation-type: tm+mt
source-git-commit: ebeca9e285af71872c05d58ba252ca65bde24f3d
workflow-type: tm+mt
source-wordcount: '259'
ht-degree: 28%

---


# CNAME實施概觀{#cname-implementation-overview}

CNAME實作可讓您自訂Adobe使用的收集網域，以符合您自己的網域。 這可讓Adobe使用JavaScript在伺服器端而非用戶端上設定第一方Cookie。 過去，這些伺服器端第一方Cookie不受Apple智慧追蹤防範(ITP)政策所限制。 但是，在2020年11月，[!DNL Apple]已更新其原則，因此這些限制也套用至透過CNAME設定的Cookie。 目前，透過CNAME在伺服器端設定的Cookie和透過Javascript在用戶端設定的Cookie，在ITP下都限制為7天或24小時到期。 有關ITP策略的詳細資訊，請參閱本[!DNL Apple]文檔[中關於跟蹤預防的](https://webkit.org/tracking-prevention/#intelligent-tracking-prevention-itp)。

雖然CNAME實作在Cookie存留期方面不提供任何好處，但可能還有其他一些好處，例如廣告封鎖程式和較不常見的瀏覽器，無法將資料傳送至他們分類為追蹤器的網域。 在這些情況下，使用CNAME可能會防止使用這些工具的使用者中斷資料收集。