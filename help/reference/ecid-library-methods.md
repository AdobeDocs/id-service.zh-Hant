---
title: Safari ITP 領域的 ECID 程式庫方法
seo-title: Safari ITP 領域的 ECID 程式庫方法
description: Adobe ECID (ID 服務) 程式庫的文件。
seo-description: Adobe ECID (ID 服務) 程式庫的文件。
translation-type: tm+mt
source-git-commit: bc5c81455023e22e64877bb861dfe141e158599c

---


# Safari ITP 領域的 ECID 程式庫方法

由於 Safari 透過 ITP 加強管制跨網域追蹤，因此 Adobe 必須持續落實程式庫最佳實務，既支援客戶又能維護消費者的隱私和選擇。

2019 年 2 月 21 日，Apple 公布了 ITP 的最新更新 (智慧防追蹤功能)。此版本詳細說明第一方 Cookie 的防追蹤新措施，有別於先前版本著重於第三方 Cookie。透過 document.cookie API 設定的所有第一方永續性 Cookie (通常稱為「用戶端」Cookie)，有效期限最多為 7 天。第三方 Cookie 將如舊版 ITP 所述，繼續遭到封鎖。For more details on ITP 2.1 and the impact of Adobe solutions, read [Safari ITP 2.1 Impact on Adobe Experience Cloud and Experience Platform Customers](https://medium.com/adobetech/safari-itp-2-1-impact-on-adobe-experience-cloud-customers-9439cecb55ac).

## Adobe ECID for Safari ITP 常見問題集

**為何 Experience Cloud ID 程式庫 (ECID) 在客戶第一方網域中設定的 AMCV Cookie，會受到 ITP 2.1 的影響?**

AMCV Cookie 目前主要依賴 document. cookie API，並透過「用戶端」設定。Safari 偏好從客戶伺服器設定的 Cookie。

**為何透過 CNAME 追蹤伺服器設定 Cookie，勝過在 Safari 中追蹤?**

ITP 的規則強調將控制權還給開發人員。透過 CNAME 憑證實作，無法單獨透過 JavaScript 完成。Adobe 的 CNAME 憑證計畫 (伺服器端追蹤) 與 ITP 一致，且多年來一直是 Adobe 策略的一部分。ECID 程式庫目前發布將 ECID 程式庫功能移至 CNAME 實作的方法。

**現今其他 Analytics 訪客追蹤方法都與 CNAME 搭配使用，為何 Adobe 反而將重心放在 ECID 程式庫?**

ECID 程式庫、AMCV Cookie 和 ECID (也稱為 MID) 一開始是一種將所有 Adobe 解決方案整合至一個 ID 下的方法。此 ID 未來在 Adobe 產品藍圖中仍會是優先 Cookie 層級 ID，現在則是 Adobe Experience Platform 的預設 Cookie ID。

**CNAME 可以協助客戶啟用多個網域追蹤嗎?**

之前與 CNAME 同時存在的規則和警告仍然存在。某些情況下，CNAME 在多重網域的案例中有其用處。如果您有一個主要進入網站，可在使用者造訪其他網域之前識別使用者的身分，那麼 CNAME 將可讓您在不接受第三方 Cookie 的瀏覽器中啟用多重網域追蹤功能。雖然 CNAME 可以在某些情況下提供多重網域協助，不過將 ECID 移轉至 CNAME 實作的原因是為了永續執行訪客身分識別，並非為了多重網域追蹤。如需深入瞭解 CNAME 和多重網域，請參閱[資料收集 CNAME 和跨網域追蹤](/help/reference/analytics-reference/cname.md)。

一有其他 ITP 變更，我們會在此處新增更多常見問題。For more inquiries, please visit [Adobe Experience League](https://experienceleague.adobe.com/#recommended/solutions/analytics).

## ITP 相關變更、方法和設定

在 Safari 中建立其他追蹤方法時，這些方法將新增於此頁面作為參考。

>以下所有文件中的 [!NOTE] *ECID* = *MID* = *MCID*。

如需 ITP 和 ECID 程式庫使用情況相關資訊，請參閱下文。

## 使用 ECID 程式庫和 CNAME 追蹤延長訪客 ID 的有效期限

ITP 2.1 會使寫入用戶端 Cookie 的能力受到限制，導致向客戶提供的訪客追蹤資訊，準確度大打折扣。因此，我們已著手調整 Adobe 的 CNAME 追蹤伺服器，將訪客的 Experience Cloud ID (ECID) 儲存在第一方 Cookie。

這項變更只適用於在第一方情境中使用 Analytics CNAME 的 ECID 客戶。如果您是尚未使用 CNAME 的 Analytics 客戶，或甚至不是 Analytics 客戶，還是符合使用 CNAME 記錄的資格。Contact Customer Care or your account representative to start the process of registering for a [CNAME](https://marketing.adobe.com/resources/help/en_US/whitepapers/first_party_cookies/adobe_managed_cert_pgm.html).

若要使用此項變更，請升級至 ECID 程式庫 4.3.0 版以上。

**設計**

對 demdex. net 提出 ID 要求並擷取 ECID 後，如果在您的 ECID 程式庫中設定追蹤伺服器，會對客戶的網域提出 ID 要求。此端點會從查詢字串讀取 eid param，並設定只包含 ECID 和兩年期限的新 [Cookie](/help/introduction/cookies.md)。每次以這種方式呼叫此端點時，`s_ecid` Cookie 的有效期限將會重新覆寫為呼叫當天的兩年後。ECID 程式庫必須更新至 4.3.0 版，才能擷取此 Cookie 的值。

這個新 `s_ecid` Cookie 會依循與 AMCV Cookie 相同的選擇退出狀態。如果從 `s_ecid` Cookie 讀取 eid，每次都會呼叫 demdex 來擷取該 ID 的最新選擇退出狀態，並將 demdex 儲存在 AMCV Cookie 中。

In addition, if your consumer has opted out of Analytics tracking via this [method](https://marketing.adobe.com/resources/help/en_US/sc/implement/opt_out_link.html), this `s_ecid` cookie will be deleted.

使用 trackingServer 或 trackingServerSecure 初始化程式庫時，應將追蹤伺服器名稱提供給 visitorJS 程式庫。此名稱應符合 Analytics 設定中的 trackingServer 設定。

如果您選擇不使用此方法，請將下列設定新增至您的 ECID 程式庫實作：discardtrackingServerCID。此設定設為 true 時，訪客程式庫不會讀取第一方追蹤伺服器設定的 MID。

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
   >如果目的地頁面已有先前瀏覽行為的 ECID，則覆寫現有 Cookie 的決定會受到此 config OverwriteRossDomainMCIDAndAID 控制。如需此設定的詳細資訊，請參閱 [OverliteRossDomainMCIDAndAID](/help/library/function-vars/overwrite-visitor-id.md)。
   >
   >如需深入瞭解此方法，請參閱 [appendVisitorIDSTO (跨網域追蹤)](/help/library/get-set/appendvisitorid.md) 參考頁面。
