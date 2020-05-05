---
description: 'null'
keywords: order of operations;ID Service
seo-description: 'null'
seo-title: 資料收集 CNAME 和跨網域追蹤
title: 資料收集 CNAME 和跨網域追蹤
uuid: ba42c822-b677-4139-b1ed-4d98d3320fd0
translation-type: tm+mt
source-git-commit: d2bc0e7fedc4e48d51f5dad158f9f8bfcb0cb4f3

---


# 資料收集 CNAME 和跨網域追蹤{#data-collection-cnames-and-cross-domain-tracking}

如果您有可在客戶造訪其他網域之前加以識別的主要進入網站，則 CNAME 將可讓您在不接受第三方 Cookie 的瀏覽器 (例如 Safari) 中使用跨網域追蹤功能。

在接受第三方Cookie的瀏覽器中，資料收集伺服器會在請求訪客ID期間設定Cookie。 此Cookie可讓訪客ID服務在使用相同Experience Cloud組織ID設定的所有網域上傳回相同的Experience Cloud訪客ID。

在拒絕協力廠商Cookie的瀏覽器中，會為每個網域指派新的Experience Cloud訪客ID。

demdex.net Cookie可讓訪客ID服務提供與Analytics中s_vi Cookie相同等級的跨網域追蹤，其中Cookie在某些瀏覽器中被接受，並跨網域使用，但被其他瀏覽器拒絕。

## Data Collection CNAMEs {#section-48fd186d376a48079769d12c4bd9f317}

When the Analytics cookie was set by the data collection server, many customers have configured data collection server CNAME records as part of a [first-party cookie implementation](https://docs.adobe.com/content/help/zh-Hant/core-services/interface/ec-cookies/cookies-first-party.html) to avoid issues with browsers that reject third-party cookies. 此程式會設定您的資料收集伺服器網域，以符合您的網站網域，讓訪客ID Cookie設為第一方Cookie。

由於訪客ID服務使用JavaScript直接在目前網站的網域上設定訪客Cookie，因此不再需要此設定來設定第一方Cookie。

具有單一 Web 屬性 (單一網域) 的客戶可從資料收集 CNAME 移轉走，改為使用其預設的資料收集主機名稱 (`omtrdc.net` 或 `2o7.net`)。

不過，在資料收集中使用CNAME還有其他好處，可讓您在不接受第三方Cookie的瀏覽器中，追蹤主要登陸網域與其他網域之間的訪客。 擁有多個Web屬性（多個網域）的客戶可能會從維護資料收集CNAME中獲益。 下節說明跨網域訪客追蹤的運作方式。

## CNAME 支援跨網域追蹤的方式 {#section-78925af798e24917b9abed79de290ad9}

由於第一方 Cookie 可在 Apple Safari 和某些其他瀏覽器中用於第三方上下文的方式，CNAME 可讓您在主要網域與其他使用相同追蹤伺服器的網域之間追蹤客戶。

例如，您在 `mymainsite.com` 有一個主要網站。您可以將 CNAME 記錄設定為指向您的安全資料收集伺服器：`smetrics.mymainsite.com`。

當使用者造訪 `mymainsite.com` 時，資料收集伺服器會設定 ID 服務 Cookie。由於資料收集伺服器的網域符合網站的網域，所以允許這個行為，這也稱為在&#x200B;*第一方內容*&#x200B;中使用 Cookie，或&#x200B;*第一方 Cookie*。

如果您也在其他網站上使用相同的資料收集伺服器 (例如 `myothersiteA.com` 和 `myothersiteB.com`)，而訪客稍後瀏覽這些網站，則在瀏覽 `mymainsite.com` 期間所設定的 Cookie 會透過 HTTPS 要求傳送給資料收集伺服器 (請記住，即使網域不符合目前網站的網域，瀏覽器仍會透過所有 HTTPS 要求將所有 Cookie 傳送至該網域)。這也稱為在&#x200B;*第三方內容*&#x200B;中使用 Cookie，或&#x200B;*第三方 Cookie*，如此可在其他網域中使用相同的訪客 ID。請注意，瀏覽器在第三方內容中處理 Cookie 的方式與第一方 Cookie 不同。

*注意：無論 Cookie 是否已設定，Safari 都會在第三方內容中封鎖所有 Cookie。*

因此，您的收集網域應該是人們經常瀏覽的網域，如此才能跨網域識別訪客。如果沒有可用於資料收集網域的&#x200B;*常見*&#x200B;網域，則維護資料收集網域的 CNAME 就無法獲得跨網域優勢。如果未先造訪主要進入網站，則訪客在次要網站與主要網站中的識別會不同。

## 使用 Experience Cloud Identity 服務啟用 CNAME 支援 {#section-25d4feb686d944e3a877d7aad8dbdf9a}

設定 `visitor.marketingCloudServerSecure` 變數即可啟用資料收集伺服器 CNAME 支援。
