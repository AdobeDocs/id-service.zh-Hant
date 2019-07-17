---
description: 'null'
keywords: 操作順序;ID 服務
seo-description: 'null'
seo-title: 資料收集 CNAME 和跨網域追蹤
title: 資料收集 CNAME 和跨網域追蹤
uuid: ba42c822-b677-4139-b1ed-4d98d3320fd0
translation-type: tm+mt
source-git-commit: e6d65f1bfed187d7440512e8f3c2de0550506c95

---


# 資料收集 CNAME 和跨網域追蹤{#data-collection-cnames-and-cross-domain-tracking}

如果您有可在客戶造訪其他網域之前加以識別的主要進入網站，則 CNAME 將可讓您在不接受第三方 Cookie 的瀏覽器 (例如 Safari) 中使用跨網域追蹤功能。

在接受第三方 Cookie 的瀏覽器中，會在訪客 ID 提出請求期間，由資料收集伺服器設定 Cookie。此 Cookie 可讓訪客 ID 服務在所有使用相同 Experience Cloud 組織 ID 設定的網域上，傳回相同的 Experience Cloud 訪客 ID。

在拒絕第三方 Cookie 的瀏覽器中，會為每個網域指派一個新的 Experience Cloud 訪客 ID。

demdex.net Cookie 可讓訪客 ID 服務提供與 Analytics 中的 s_vi Cookie 相同層級的跨網域追蹤，其中，有些瀏覽器會接受 Cookie 並跨網域使用，有些瀏覽器則會拒絕。

## 資料收集 CNAME {#section-48fd186d376a48079769d12c4bd9f317}

在資料收集伺服器設定 Analytics Cookie 時，許多客戶都將資料收集伺服器 CNAME 記錄設定為[第一方 Cookie 實作](https://marketing.adobe.com/resources/help/en_US/whitepapers/first_party_cookies/)的一部分，以避免發生瀏覽器拒絕第三方 Cookie 的問題。此程序會將您的資料收集伺服器網域設定為符合您的網站網域，使訪客 ID Cookie 設為第一方 Cookie。

由於訪客 ID 服務會將訪客 Cookie 直接設定在目前使用 JavaScript 之網站的網域上，因此在設定第一方 Cookie 時已不需要此設定。

具有單一 Web 屬性 (單一網域) 的客戶可從資料收集 CNAME 移轉走，改為使用其預設的資料收集主機名稱 (`omtrdc.net` 或 `2o7.net`)。

但在資料收集中使用 CNAME 具有附帶好處，而可讓您在不接受第三方 Cookie 之瀏覽器中的主要登陸網域與其他網域之間追蹤訪客。具有多個 Web 屬性 (多個網域) 的客戶可能會因為保持使用資料收集 CNAME 而獲益。下一節說明跨網域訪客如何進行追蹤。

## CNAME 支援跨網域追蹤的方式 {#section-78925af798e24917b9abed79de290ad9}

由於第一方 Cookie 可在 Apple Safari 和某些其他瀏覽器中用於第三方上下文的方式，CNAME 可讓您在主要網域與其他使用相同追蹤伺服器的網域之間追蹤客戶。

例如，您在 `mymainsite.com` 有一個主要網站。您可以將 CNAME 記錄設定為指向您的安全資料收集伺服器: `smetrics.mymainsite.com`。

當使用者造訪 `mymainsite.com` 時，資料收集伺服器會設定 ID 服務 Cookie。由於資料收集伺服器的網域符合網站的網域，所以允許這個行為，這也稱為在&#x200B;*第一方內容*&#x200B;中使用 Cookie，或&#x200B;*第一方 Cookie*。

如果您也在其他網站上使用相同的資料收集伺服器 (例如 `myothersiteA.com` 和 `myothersiteB.com`)，而訪客稍後瀏覽這些網站，則在瀏覽 `mymainsite.com` 期間所設定的 Cookie 會透過 HTTPS 要求傳送給資料收集伺服器 (請記住，即使網域不符合目前網站的網域，瀏覽器仍會透過所有 HTTPS 要求將所有 Cookie 傳送至該網域)。這也稱為在&#x200B;*第三方內容*&#x200B;中使用 Cookie，或&#x200B;*第三方 Cookie*，如此可在其他網域中使用相同的訪客 ID。請注意，瀏覽器在第三方內容中處理 Cookie 的方式與第一方 Cookie 不同。

*注意: 無論 Cookie 是否已設定，Safari 都會在第三方內容中封鎖所有 Cookie。*

因此，您的收集網域應該是人們經常瀏覽的網域，如此才能跨網域識別訪客。如果沒有可用於資料收集網域的&#x200B;*常見*&#x200B;網域，則維護資料收集網域的 CNAME 就無法獲得跨網域優勢。如果未先造訪主要進入網站，則訪客在次要網站與主要網站中的識別會不同。

## Enable CNAME support with the Experience Cloud Identity Service {#section-25d4feb686d944e3a877d7aad8dbdf9a}

設定 `visitor.marketingCloudServerSecure` 變數即可啟用資料收集伺服器 CNAME 支援。
