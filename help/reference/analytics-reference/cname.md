---
description: 'null'
keywords: order of operations;ID Service
seo-description: 'null'
seo-title: 資料收集 CNAME 和跨網域追蹤
title: 資料收集 CNAME 和跨網域追蹤
uuid: ba42c822-b677-4139-b1ed-4d98d3320fd0
translation-type: tm+mt
source-git-commit: 9fe63cf3983a2ed6642837b02a3c3441ef745d70
workflow-type: tm+mt
source-wordcount: '602'
ht-degree: 100%

---


# 資料收集 CNAME 和跨網域追蹤{#data-collection-cnames-and-cross-domain-tracking}

如果您有可在客戶造訪其他網域之前加以識別的主要進入網站，則 CNAME 將可讓您在不接受第三方 Cookie 的瀏覽器 (例如 Safari) 中使用跨網域追蹤功能。

在接受第三方 Cookie 的瀏覽器中，資料收集伺服器會在請求訪客 ID 期間設定 Cookie。此 Cookie 可讓訪客 ID 服務在所有使用相同 Experience Cloud 組織 ID 設定的網域上，傳回相同的 Experience Cloud 訪客 ID。

在拒絕第三方 Cookie 的瀏覽器中，會為每個網域指派新的 Experience Cloud 訪客 ID。

demdex.net Cookie 可讓訪客 ID 服務提供與 Analytics 中的 s_vi Cookie 相同層級的跨網域追蹤，此時，Cookie 在部分瀏覽器中會被接受，並跨網域使用，但會被其他瀏覽器拒絕。

## 資料收集 CNAME{#section-48fd186d376a48079769d12c4bd9f317}

在 Analytics Cookie 由資料收集伺服器所設定時，許多客戶都會將資料收集伺服器 CNAME 記錄設定為[第一方 Cookie 實作](https://docs.adobe.com/content/help/zh-Hant/core-services/interface/ec-cookies/cookies-first-party.html)的一部分，以避免發生瀏覽器拒絕第三方 Cookie 的問題。此程序會將您的資料收集伺服器網域設定為符合網站網域，以便將訪客 ID Cookie 設定為第一方 Cookie。

由於訪客 ID 服務會使用 JavaScript 直接在現行網站的網域上設定訪客 Cookie，因此不再需要以此設定來設定第一方 Cookie。

具有單一 Web 屬性 (單一網域) 的客戶可從資料收集 CNAME 移轉走，改為使用其預設的資料收集主機名稱 (`omtrdc.net` 或 `2o7.net`)。

不過，在資料收集中使用 CNAME 還有其他好處，可讓您在主要登陸網域與不接受第三方 Cookie 的瀏覽器中的其他網域之間追蹤訪客。具有多個 Web 屬性 (多個網域) 的客戶，可藉由維護資料收集 CNAME 而獲益。下一節將說明跨網域訪客追蹤的運作方式。

## 跨網域追蹤{#section-78925af798e24917b9abed79de290ad9}

如果使用者的隱私權和瀏覽器設定允許，訪客 ID 服務將會以 demdex.net 作為其網域，進行跨網域 (但位於同一家所屬公司內) 的訪客追蹤。

CNAME 並未提供其他跨網域的優點。例如，您在 `mymainsite.com` 有一個主要網站。您可以將 CNAME 記錄設定為指向您的安全資料收集伺服器：`smetrics.mymainsite.com`。

當使用者造訪 `mymainsite.com` 時，資料收集伺服器會設定 ID 服務 Cookie。由於資料收集伺服器的網域符合網站的網域，所以允許這個行為，這也稱為在&#x200B;*第一方內容*&#x200B;中使用 Cookie，或&#x200B;*第一方 Cookie*。

如果您也在其他網站上使用相同的資料收集伺服器 (例如 `myothersiteA.com` 和 `myothersiteB.com`)，而訪客稍後瀏覽這些網站，則在瀏覽 `mymainsite.com` 期間所設定的 Cookie 會透過 HTTPS 要求傳送給資料收集伺服器 (請記住，即使網域不符合目前網站的網域，瀏覽器仍會透過所有 HTTPS 要求將所有 Cookie 傳送至該網域)。這就是所謂的在&#x200B;*第三方內容*&#x200B;中使用 Cookie，或使用&#x200B;*第三方 Cookie* (即使您使用 CNAME)。Adobe 建議將 CNAME 用於每個唯一網域。

*注意：無論 Cookie 是否已設定，Safari 都會在第三方內容中封鎖所有 Cookie。*

## 使用 Experience Cloud Identity Service 啟用 CNAME 支援 {#section-25d4feb686d944e3a877d7aad8dbdf9a}

設定 `visitor.marketingCloudServerSecure` 變數即可啟用資料收集伺服器 CNAME 支援。
