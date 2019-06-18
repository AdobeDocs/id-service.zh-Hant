---
title: Safari ITP世界中的ECID程式庫方法
seo-title: Safari ITP世界中的ECID程式庫方法
description: Adobe ECID(ID服務)程式庫的文件。
seo-description: Adobe ECID(ID服務)程式庫的文件。
translation-type: tm+mt
source-git-commit: 1dd8b109f7e9567b5f72747ecc653d35d0942413

---


# Safari ITP世界中的ECID程式庫方法

當Safari透過ITP強化跨網域追蹤時，Adobe必須維護支援客戶以及消費者隱私權和選擇的程式庫最佳做法。

Apple於2019年月21日推出ITP最新更新(智慧追蹤防止)。不同於先前針對第三方Cookie的版本，本版本詳細說明第一方Cookie的新追蹤防範措施。所有透過document. cookie API(通常稱為「用戶端」Cookie)設定的第一方永久性Cookie，都會在天內暫停。第三方Cookie將繼續遭到封鎖，如舊版ITP中所述。如需IDP2.1的詳細資訊以及Adobe解決方案的影響，請閱讀 [Safari ITP2.1對Adobe Experience Cloud和Experience Platform客戶](https://medium.com/adobetech/safari-itp-2-1-impact-on-adobe-experience-cloud-customers-9439cecb55ac)的影響。

## Safari ITP常見問答集的Adobe ECID

**為甚麼AMCV Cookie是由客戶的第一方網域(受ITP2.1影響)所設定的AMCV Cookie設定？**

AMCV Cookie目前依賴document. cookie API，並透過「用戶端」設定。Safari偏好從客戶伺服器設定的Cookie。

**為甚麼透過CNAME追蹤伺服器設定Cookie，更適合在Safari中追蹤？**

ITP的規則著重於給予開發人員掌控權。透過CNAME憑證實施無法單獨透過JavaScript完成。Adobe CNAME認證計劃(伺服器端追蹤)與ITP一致，多年來一直屬於Adobe策略的一部分。ECID程式庫是將ECID程式庫功能移至CNAME實作的發佈方法。

**當現今的Analytics訪客追蹤方法與CNAME搭配使用時，為何Adobe會專注於ECID程式庫？**

ECID程式庫、AMCV Cookie和ECID(也稱為MID)是將所有Adobe解決方案整合在一個ID之下的方法。此ID將繼續是Adobe產品藍圖中的優先Cookie層級ID，也是Adobe Experience Platform的預設Cookie ID。

**CNAME是否可協助客戶進行多網域追蹤？**

先前包含CNAME先前存在的規則和警告仍然存在。在某些情況下，CNAME可協助多網域藍本。如果您有一個主要進入網站，可在訪客瀏覽其他網域之前加以識別，則CNAME可在不接受第三方Cookie的瀏覽器中啓用多網域追蹤。然而，雖然CNAME在某些情況下可提供多網域協助，但ECID將ECID移轉至CNAME實作的原因是持續的訪客識別，而非多網域追蹤。如需CNAME和多網域的詳細資訊，請參閱 [資料收集CNAME和跨網域追蹤](/help/mcvid-reference/mcvid-analytics-reference/mcvid-cname.md)。

當額外的ITP變更發行時，將會新增更多常見問題。若需更多諮詢，請造訪 [Adobe Experience League](https://experienceleague.adobe.com/#recommended/solutions/analytics)。

## ITP相關變更、方法和組態

在Safari中建立其他方法以追蹤時，將會新增為此頁面的參考。

>[!NOTE]*ECID* = *MID* = *MID* = MID= MID。

請參閱以下有關ITP和ECID程式庫使用情形的相關努力。

## 使用ECID程式庫和CNAME追蹤來延長訪客ID有效期

ITP2.1阻礙編寫用戶端Cookie的能力，因而削弱了提供準確訪客追蹤資訊的能力。因此，Adobe的CNAME追蹤伺服器會推出變更，將訪客的Experience Cloud ID(ECID)儲存在第一方Cookie中。

這項變更只適用於在第一方上下文中使用Analytics CNAME的ECID客戶。如果您是目前未使用CNAME的Analytics客戶，或是非Analytics客戶，則您仍然符合CNAME記錄的資格。請聯絡客戶服務或您的帳戶代表，開始註冊 [CNAME](https://marketing.adobe.com/resources/help/en_US/whitepapers/first_party_cookies/adobe_managed_cert_pgm.html)。

升級至ECID程式庫v4.3.0+以利用此項變更。

**設計**

在對demdex. net提出ID要求並擷取ECID後，如果在您的ECID程式庫中設定追蹤伺服器，則會對客戶的網域提出ID要求。This endpoint reads the ecid param from the query string, and sets a new [cookie](/help/mcvid-introduction/mcvid-cookies.md) that comprises only the ECID and an expiration date two years in the future. 每次以這種方式呼叫此端點時， `s_ecid` 會以兩年期間的有效期來重寫Cookie。ECID程式庫必須更新至v4.3.0，才能擷取此Cookie的值。

此新 `s_ecid` Cookie會遵循與AMCV Cookie相同的退出狀態。如果從 `s_ecid` Cookie讀取eid，則一律會呼叫demdex來擷取該ID的最新退出狀態，並儲存在AMCV Cookie中。

此外，如果您的消費者已透過此 [方法](https://marketing.adobe.com/resources/help/en_US/sc/implement/opt_out_link.html)選擇退出Analytics追蹤，則會刪除此 `s_ecid` Cookie。

使用trackingServer或trackingServerSecure初始化程式庫時，應將追蹤伺服器名稱提供給visitorJS程式庫。這應該符合Analytics設定中的trackingServer設定。

如果您選擇不運用此方法，請將下列組態新增至您的ECID程式庫實施：discardtrackingServerCID。當此組態設定為true時，訪客程式庫不會讀取第一方追蹤伺服器所設定的MID。

![](assets/itp-proposal-v1.png)

## 使用appendVisitorIDSTO方法進行跨網域追蹤(在您自己公司的多個網域內)

當瀏覽器封鎖第三方Cookie時，此函數可讓您跨網域共用訪客的ECID。若要使用此函數，您必須先實施 ID 服務，且擁有來源和目的地的網域。可在VisitorAPI. js1.7.0版或更新版本中使用(但不適用於1.10.0版)。

**設計**

* 當訪客瀏覽至您的其他網域時，Visitor. appendVisitorIDSTO(url)會傳回包含附加為查詢參數之ECID的URL。

   使用此URL從原始網域重新導向至目的地網域。

* 目的地網域上的ID服務程式碼會從URL擷取ECID，而不是向Adobe傳送請求給Adobe的ID。

   此要求包含第三方 Cookie ID，而該 ID 在此案件中無法使用。

* 目的地頁面上的ID服務程式碼使用傳入的ECID來追蹤訪客。

   >[!NOTE]
   >如果目的地頁面已有先前瀏覽的ECID，則覆寫現有Cookie的決定會受到此config OverwriteRossDomainMCIDAndAID的控制。如需此組態的詳細資訊，請參閱 [OverliteRossDomainMCIDAndAID](/help/mcvid-library/mcvid-function-vars/mcvid-overwrite-visitor-id.md)。
   >
   >如需此方法的詳細資訊，請參閱 [appendVisitorIDSTO(跨網域追蹤)](/help/mcvid-library/mcvid-get-set/mcvid-appendvisitorid.md) 參考頁面。
