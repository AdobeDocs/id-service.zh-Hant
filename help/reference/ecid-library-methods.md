---
title: Safari ITP 領域的 ECID 程式庫方法
seo-title: Safari ITP 領域的 ECID 程式庫方法
description: Adobe ECID (ID 服務) 程式庫的文件。
seo-description: Adobe ECID (ID 服務) 程式庫的文件。
translation-type: tm+mt
source-git-commit: 012bf5db473b37b17e7af957c08da71b253c718f
workflow-type: tm+mt
source-wordcount: '810'
ht-degree: 72%

---


# Safari ITP 領域的 ECID 程式庫方法

>[!NOTE]
>
>已進行更新，以反映2020年11月12日發佈的ITP最新變更，這是Big Sur OS版本的一部分。

由於 Safari 透過 ITP 加強管制跨網域追蹤，因此 Adobe 必須持續落實程式庫最佳實務，既支援客戶又能維護消費者的隱私和選擇。

自2020年11月10日起，所有透過document.cookie API（通常稱為「用戶端」Cookie）設定的第一方永久性Cookie，以及透過Safari和行動iOS瀏覽器中第一方CNAME實作所設定的Cookie，其過期限制為7天。 如舊版ITP中所述，第三方Cookie將繼續遭到封鎖。 如需深入了解 ITP 2.1 及 Adobe 解決方案的影響，請參閱 [Safari ITP 2.1 對 Adobe Experience Cloud 和 Experience Platform Customers 的影響](https://medium.com/adobetech/safari-itp-2-1-impact-on-adobe-experience-cloud-customers-9439cecb55ac)。

## ITP相關更改、方法和配置

在 Safari 中建立其他追蹤方法時，這些方法將新增於此頁面作為參考。

>[!NOTE]
>
>以下所有文件中的 *ECID* = *MID* = *MCID*。

如需 ITP 和 ECID 程式庫使用情況相關資訊，請參閱下文。

## 目前ITP和Apple WebKit的ECID程式庫行為

ITP 2.1 會使寫入用戶端 Cookie 的能力受到限制，導致向客戶提供的訪客追蹤資訊，準確度大打折扣。因此，Adobe的CNAME追蹤伺服器中會引入變更，將訪客的Experience Cloud ID(ECID)儲存在第一方Cookie中。

這項變更只適用於在第一方情境中使用 Analytics CNAME 的 ECID 客戶。如果您是尚未使用 CNAME 的 Analytics 客戶，或甚至不是 Analytics 客戶，還是符合使用 CNAME 記錄的資格。請連絡客戶服務或您的客戶代表，以開始 [CNAME](https://docs.adobe.com/content/help/zh-Hant/core-services/interface/ec-cookies/cookies-first-party.html) 的註冊程序。

若要使用此項變更，請升級至 ECID 程式庫 4.3.0 版以上。

以下概述ECID程式庫與ITP 2.1的運作方式，以及Apple在Big Surr版本中所做的最新變更

**設計**

對 demdex. net 提出 ID 要求並擷取 ECID 後，如果在您的 ECID 程式庫中設定追蹤伺服器，會對客戶的網域提出 ID 要求。此端點會從查詢字串讀取 eid param，並設定只包含 ECID 和兩年期限的新 [Cookie](/help/introduction/cookies.md)。每次以這種方式呼叫此端點時，`s_ecid` Cookie 的有效期限將會重新覆寫為呼叫當天的兩年後。ECID 程式庫必須更新至 4.3.0 版，才能擷取此 Cookie 的值。

>[!IMPORTANT]
>
>Big Sur更新中，透過CNAME設 `s_ecid` 定的Cookie也會持續7天。

這個新 `s_ecid` Cookie 會依循與 AMCV Cookie 相同的選擇退出狀態。如果從 `s_ecid` Cookie 讀取 eid，每次都會呼叫 demdex 來擷取該 ID 的最新選擇退出狀態，並將 demdex 儲存在 AMCV Cookie 中。

此外，如果您的消費者已透過此[方法](https://docs.adobe.com/content/help/zh-Hant/analytics/implementation/js/opt-out.html)選擇退出 Analytics 追蹤，則系統會刪除這個 `s_ecid` Cookie。

The tracking server name should be supplied to the VisitorJS library when initializing the library using `trackingServer` or `trackingServerSecure`. This should match the `trackingServer` config in the Analytics configs.

If you choose not to take advantage of this method, add the following config to your ECID library implementation: `discardtrackingServerECID`. 當此設定設為true時，訪客庫不會讀取第一方追蹤伺服器所設定的MID。

![](assets/itp-proposal-v1.png)

## 使用 appendVisitorIDsTo 方法執行跨網域追蹤 (在自己公司的多個網域內)

瀏覽器封鎖第三方 Cookie 時，此函數可讓您跨網域共用訪客的 ECID。若要使用此函數，您必須先實作 ID 服務，且擁有來源和目的地的網域。此函數可在 VisitorAPI. js 1.7.0 版或更新版本中使用 (但不適用於 1.10.0 版)。

**設計**

* 訪客瀏覽至您的其他網域時，Visitor.appendVisitorIDsTo(url) 會傳回一個附加 ECID 作為查詢參數的 URL。

   使用此 URL 可從原始網域重新導向至目的地網域。

* 目的地網域的 ID 服務程式碼會從 URL 提取 ECID，而非傳送要求向 Adobe 索取該訪客的 ID。

   此要求包含第三方 Cookie ID，而該 ID 在此案件中無法使用。

* 目的地頁面上的 ID 服務程式碼會使用傳入的 ECID 追蹤訪客。

   >[!NOTE]
   >如果目的地頁面已有先前瀏覽行為的 ECID，則覆寫現有 Cookie 的決定會受到此 config overwriteCrossDomainMCIDAndAID 控制。如需此設定的詳細資訊，請參閱 [overwriteCrossDomainMCIDAndAID](/help/library/function-vars/overwrite-visitor-id.md)。
   >
   >如需深入了解此方法，請參閱 [appendVisitorIDsTo (跨網域追蹤)](/help/library/get-set/appendvisitorid.md) 參考頁面。
