---
description: 關於搭配 Experience Cloud Identity 服務使用 Analytics 的功能、功用和問題之常見問題集。
keywords: Experience Cloud Identity Service
seo-description: 關於搭配 Identity 服務使用 Analytics 的功能、功用和問題之常見問題集。
seo-title: Analytics 與 Identity 服務常見問題集
title: Analytics 與 Identity 服務常見問題集
uuid: 35ed79a9-eccc-4b54-8451-606f091c73b7
translation-type: tm+mt
source-git-commit: d2bc0e7fedc4e48d51f5dad158f9f8bfcb0cb4f3

---


# Analytics 與 Identity 服務常見問題集{#analytics-and-id-service-faqs}

關於搭配 Identity 服務使用 Analytics 的功能、功用和問題之常見問題集。

## 追蹤伺服器 {#section-9a2ad7842e364c869e1650480d17f8ef}

**如何找到追蹤伺服器資訊？**

每個正確設定的AppMeasurement代碼都包含您的追蹤伺服器資訊。

不過，有時客戶可能會將其Analytics AppMeasurement檔案分割為個別檔案。 例如，有些客戶可能會將組態變數放入一個檔案中、使用第二個檔案做為外掛程式，然後將AppMeasurement程式碼放入第三個檔案中。 不建議使用。

如果您找不到追蹤伺服器資訊，則Analytics例項可能無法正確設定。 如果您 [找不到追蹤伺服器](https://helpx.adobe.com/tw/marketing-cloud/contact-support.html) ，請連絡客戶服務。

**如果我使用 Identity 服務並變更追蹤伺服器，會發生什麼事?**

已由 Identity 服務識別的使用者不會有任何變化。尚未移轉至 Identity 服務且仍由 Analytics Cookie 識別的舊版訪客則有影響。受影響的使用者人數，取決於 Identity 服務已生效多久。例如，Identity 服務已生效 1 星期的實作中，舊版訪客可能多於 Identity 服務已生效 6 個月的實作，因為當使用者返回網站時就已經經過移轉了。

## 實作與設定 {#section-6028f55d5b514ae6a631c6a79f42fb89}

**我是否必須設定CNAME以追蹤跨網域的訪客？**

如果您有可在客戶造訪其他網域之前加以識別的主要進入網站，則 CNAME 將可讓您在不接受第三方 Cookie 的瀏覽器 (例如 Safari) 中使用跨網域追蹤功能。

In browsers that accept third-party cookies, a cookie is set in the [demdex.net domain](https://docs.adobe.com/content/help/zh-Hant/audience-manager/user-guide/reference/demdex-calls.html) during the request to retrieve a visitor ID. 此 Cookie 可讓 Identity 服務在所有使用相同組織 ID 設定的網域上，傳回相同的 Experience Cloud 訪客 ID。在拒絕協力廠商Cookie的瀏覽器中，會為每個網域指派新的Experience Cloud訪客ID。

即使已設定CNAME，若未先瀏覽主要登入網站，在不接受第三方Cookie的瀏覽器中，訪客在次要網站和主要網站上的識別也會有所不同。

**為什麼Experience Cloud ID(MID)參數不在Analytics請求中？**

如果 Identity 服務正確傳回資訊，但您未看見 `MID` 參數，請確定您已升級至 AppMeasurement 的支援版本。

**我的網站是否可搭配 Identity 服務使用 H 程式碼和 JavaScript 適用的 AppMeasurement?**

是。只要這兩個檔案都參照相同的VisitorAPI.js檔案，您就可以在網站上混合使用H程式碼和JavaScript適用的AppMeasurement。

不過，visitorAPI.js程式碼1.6版或更新版本不支援H程式碼。 如果您想要升級至visitorAPI.js 1.6版（或更新版本），則無法繼續使用H程式碼。

**什麼是寬限期，我要如何設定？**

參閱 [ Identity 服務寬期限](../reference/analytics-reference/grace-period.md)並聯絡[客戶服務](https://helpx.adobe.com/tw/marketing-cloud/contact-support.html)。

**為什麼我需要移轉至即時資料蒐集 (RDC) 才能使用 Identity 服務?**

RDC 可以提升全域效能，此外為了確保您的實作可針對未來採用 Adobe 頂尖全域網路的功能做好準備，也有需要進行 RDC 移轉。See [Analytics Requirements: Regional Data Collection (RDC)](../reference/requirements.md#section-7d04bb013bc84a25bae3b148bc0ca25f).

## 報告 {#section-123cd55a32e54a45a23beb140becfa8f}

**搭配 Identity 服務使用 Analytics 而造成的不一致，有哪些可能的原因?**

使用 Identity 服務時，發生不一致的常見原因包括:

* 持續使用舊版s_vi Cookie。 這造成資料收集不一致。
* 在訪客從調查導覽至快顯時重複計算訪客。

## Cookie {#section-b7d5384fbedd47b09e1030211c39a3d1}

**如果 Identity 服務無法設定 AMCV Cookie，Analytics 中會發生什麼事?**

有三種可能的情形會影響新訪客的Analytics資料：

1. 使用者在AMCV Cookie設定成功之前離開頁面（在30秒逾時視窗內）。

   如果訪客在載入完成前離開頁面，則不會傳送Analytics點擊。 Analytics不會從此藍本收到資料，並會認為資料會因頁面提早關閉而遺失。 根據我們的測試（包括邊遠地區），我們發現此藍本平均佔流量的比例不到1%。 需要注意的是，即使未提供 Identity 服務，這種情況也會出現；這是將 Analytics 資料收集程式碼包含在頁面底部的一種工具。

1. 由於連接速度緩慢或瀏覽器「旋轉」，終端使用者在 30 秒逾時範圍內未獲得指派 Identity 服務或 Analytics ID。

   Identity 服務和 Analytics ID 均未設定，系統將分配一個用戶端 ID 給訪客。雖然這可以擷取Analytics資料，但當訪客在後續頁面上設定Analytics ID時，訪客的描述檔將會中斷。 用戶端ID也不會與Audience Manager或Analytics中儲存的任何現有訪客資料相符。 如果兩個不同的網域正傳送至相同的報表套裝，此用戶端ID也會在Analytics中顯示為兩個不同的訪客。

1. 終端使用者在 30 秒逾時範圍內未獲得分配 Identity 服務 ID，但會獲得分配標準 Analytics 追蹤 ID，而且不會啟用寬限期。

   情況 3 與情況 2 的結果相同，即皆使用基於用戶端的 ID。

>[!TIP]
>
>搭配預設設定使用最新的 VisitorAPI.js 和 AppMeasurement.js 時，應避免上述三種罕見情況所造成的嚴重或明顯影響。

>[!MORELIKETHIS]
>
>* [客戶服務](https://helpx.adobe.com/tw/marketing-cloud/contact-support.html)

