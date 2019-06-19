---
description: 有關搭配 ID 服務使用 Analytics 的相關功能和問題的常見問題。
keywords: ID 服務
seo-description: 有關搭配 ID 服務使用 Analytics 的相關功能和問題的常見問題。
seo-title: Analytics 與 ID 服務常見問題
title: Analytics 與 ID 服務常見問題
uuid: 35ed79a9-ecc-4b54-8451-606f091 c73 b7
translation-type: tm+mt
source-git-commit: bc5c81455023e22e64877bb861dfe141e158599c

---


# Analytics 與 ID 服務常見問題{#analytics-and-id-service-faqs}

有關搭配 ID 服務使用 Analytics 的相關功能和問題的常見問題。

## 追蹤伺服器 {#section-9a2ad7842e364c869e1650480d17f8ef}

**我該如何找到追蹤伺服器資訊?**

每一條正確設定的 AppMeasurement 程式碼都包含您的追蹤伺服器資訊。

然而，有時候客戶會將 Analytics AppMeasurement 檔案分割成個別的檔案。舉例來說，有些客戶可能會在一個檔案中放置設定變數，然後使用第二個檔案放置外掛程式，接著再將 AppMeasurement 程式碼放到第三個檔案。我們建議您不要這麼做。

如果您無法找到自己的追蹤伺服器資訊，則您的 Analytics 例項可能並未正確設定。如果您找不到自己的追蹤伺服器資訊，請聯絡[客戶服務](https://helpx.adobe.com/marketing-cloud/contact-support.html)。

**如果我使用 ID 服務並變更追蹤伺服器，會發生什麼事?**

已由 ID 服務識別的使用者不會有任何變化。尚未移轉至 ID 服務且仍由 Analytics Cookie 識別的舊版訪客則有影響。受影響的使用者人數，取決於 ID 服務已生效多久。例如，ID 服務已生效 1 星期的實施中，舊版訪客可能多於 ID 服務已生效 6 個月的實施，因為當使用者返回網站時就已經經過移轉了。

## 實作與組態配置 {#section-6028f55d5b514ae6a631c6a79f42fb89}

**是否需要設定 CNAME 才能跨網域追蹤訪客?**

如果您有可在客戶造訪其他網域之前加以識別的主要進入網站，則 CNAME 將可讓您在不接受第三方 Cookie 的瀏覽器 (例如 Safari) 中使用跨網域追蹤功能。

在接受第三方 Cookie 的瀏覽器中，[demdex.net 網域](https://marketing.adobe.com/resources/help/en_US/aam/demdex-calls.html)會在要求擷取訪客 ID 期間設定 Cookie。此 Cookie 可讓訪客 ID 服務在所有使用相同組織 ID 設定的網域上，傳回相同的 Experience Cloud 訪客 ID。在拒絕第三方 Cookie 的瀏覽器中，會為每個網域指派一個新的 Experience Cloud 訪客 ID。

即使已設定 CNAME，如果未先造訪主要進入網站，則在不接受第三方 Cookie 的瀏覽器中將會以不同的方式識別次要網站與主要網站中的訪客。

**為何 Experience Cloud ID (MID) 參數不在 Analytics 要求中?**

如果 ID 服務正確傳回資訊，但您未看見 `MID` 參數，請確定您已升級至 AppMeasurement 的支援版本。

**我的網站是否可搭配 ID 服務使用 H 程式碼和 JavaScript 適用的 AppMeasurement?**

可以。只要兩個檔案參照相同的 VisitorAPI.js 檔案，您即可在網站上混用 H 程式碼和 JavaScript 適用的 AppMeasurement。

但是，visitorAPI.js code 1.6 版或更新版本不支援 H 程式碼。如果您想升級至 visitorAPI.js v 1.6 (或更新版本)，將無法繼續使用 H 程式碼。

**什麼是寬限期以及我該如何設定寬限期?**

請參閱 [ID服務寬限期](../reference/analytics-reference/grace-period.md) ，並聯絡 [客戶服務](https://helpx.adobe.com/marketing-cloud/contact-support.html)。

**為什麼我需要移轉至即時資料蒐集 (RDC) 才能使用 ID 服務?**

RDC 可以提升全域效能，此外為了確保您的實施可針對未來採用 Adobe 頂尖全域網路的功能做好準備，也有需要進行 RDC 移轉。請參閱 [Analytics 需求: 地區資料收集 (RDC)](../reference/requirements.md#section-7d04bb013bc84a25bae3b148bc0ca25f)。

## 報告 {#section-123cd55a32e54a45a23beb140becfa8f}

**搭配 ID 服務使用 Analytics 而造成的不一致，有哪些可能的原因?**

使用 ID 服務時，發生不一致的常見原因包括:

* 繼續使用舊有的 s_vi Cookie。這造成了資料蒐集的不一致。
* 當訪客從調查導覽至彈出式視窗時發生重複計數訪客。

## Cookie {#section-b7d5384fbedd47b09e1030211c39a3d1}

**如果 ID 服務無法設定 AMCV Cookie，Analytics 中會發生什麼事?**

有三種潛在情形會影響新訪客的 Analytics 資料:

1. 終端使用者在 AMCV Cookie 成功設定之前離開頁面 (在 30 秒的逾時範圍內)。

   如果訪客在頁面載入完成之前離開，則不會傳送 Analytics 點擊資訊。Analytics 不會收到這種情況下產生的資料，並且會將該資料視為因網頁提前關閉而遺失。根據我們的測試，其中包括外圍地理位置，我們發現此狀況的平均流量不到 1％。請務必注意，即使沒有MCID服務，此情況有時也會發生-這是將Analytics資料收集程式碼加入頁面底部的一個事實。

1. 由於連接速度緩慢或瀏覽器「旋轉」，終端使用者在 30 秒逾時範圍內未獲得指派 ID 服務或 Analytics ID。

   ID 服務和 Analytics ID 均未設定，系統將分配一個用戶端 ID 給訪客。這種作法雖然可以擷取 Analytics 資料，但在後續頁面上設定 Analytics ID 時，訪客的個人資料檔將會中斷而不完整。用戶端 ID 也不會與 Audience Manager 或 Analytics 中存儲的任何現有的訪客設定檔相匹配。如果將兩個單獨的網域傳送至相同的報表套件，此用戶端 ID 在 Analytics 中也會顯示為兩個不同的訪客。

1. 終端使用者在 30 秒逾時範圍內未獲得分配 ID 或服務 ID，但會獲得分配標準 Analytics 追蹤 ID，而且不會啟用寬限期。

   情況 3 與情況 2 的結果相同，即皆使用基於用戶端的 ID。

>[!TIP]
>
>使用預設設定對VisitorAPI. js和AppMeasurement. js的最新更新，應避免上述三種可能發生的嚴重或顯著影響。

>[!MORE_贊_ this]
>
>* [客戶服務](https://helpx.adobe.com/marketing-cloud/contact-support.html)

