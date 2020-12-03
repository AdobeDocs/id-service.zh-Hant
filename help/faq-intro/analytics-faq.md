---
description: 關於搭配 Experience Cloud Identity Service 使用 Analytics 的功能、功用和問題之常見問題集。
keywords: Experience Cloud Identity Service
seo-description: 關於搭配 Identity Service 使用 Analytics 的功能、功用和問題之常見問題集。
seo-title: Analytics 與 Identity Service 常見問題集
title: Analytics 與 Identity Service 常見問題集
uuid: 35ed79a9-eccc-4b54-8451-606f091c73b7
translation-type: tm+mt
source-git-commit: d2bc0e7fedc4e48d51f5dad158f9f8bfcb0cb4f3
workflow-type: tm+mt
source-wordcount: '989'
ht-degree: 100%

---


# Analytics 與 Identity Service 常見問題集{#analytics-and-id-service-faqs}

關於搭配 Identity Service 使用 Analytics 的功能、功用和問題之常見問題集。

## 追蹤伺服器 {#section-9a2ad7842e364c869e1650480d17f8ef}

**如何尋找我的追蹤伺服器資訊？**

每一段正確設定的 AppMeasurement 程式碼都包含您的追蹤伺服器資訊。

不過，有時客戶可能會將其 Analytics AppMeasurement 檔案分割為個別檔案。例如，有些客戶可能會將設定變數放在一個檔案中、使用第二個檔案處理外掛程式，並將 AppMeasurement 程式碼放在第三個檔案中。不建議採用此做法。

如果您找不到追蹤伺服器資訊，表示您的 Analytics 例項可能未正確設定。如果您找不到追蹤伺服器，請聯絡[客戶服務](https://helpx.adobe.com/tw/marketing-cloud/contact-support.html)。

**如果我使用 Identity Service 並變更追蹤伺服器，會發生什麼事？**

已由 Identity Service 識別的使用者不會有任何變化。尚未移轉至 Identity Service 且仍由 Analytics Cookie 識別的舊版訪客則有影響。受影響的使用者人數，取決於 Identity Service 已生效多久。例如，Identity Service 已生效 1 星期的實作中，舊版訪客可能多於 Identity Service 已生效 6 個月的實作，因為當使用者返回網站時就已經經過移轉了。

## 實作與設定 {#section-6028f55d5b514ae6a631c6a79f42fb89}

**我是否必須設定 CNAME 以追蹤各網域間的訪客？**

如果您有可在客戶造訪其他網域之前加以識別的主要進入網站，則 CNAME 將可讓您在不接受第三方 Cookie 的瀏覽器 (例如 Safari) 中使用跨網域追蹤功能。

在接受第三方 Cookie 的瀏覽器中，請求擷取訪客 ID 期間，Cookie 會設定於 [demdex.net 網域](https://docs.adobe.com/content/help/zh-Hant/audience-manager/user-guide/reference/demdex-calls.html)中。此 Cookie 可讓 Identity Service 在所有使用相同組織 ID 設定的網域上，傳回相同的 Experience Cloud 訪客 ID。在拒絕第三方 Cookie 的瀏覽器中，會為每個網域指派新的 Experience Cloud 訪客 ID。

即使已設定 CNAME，若未先造訪主要進入網站，在不接受第三方 Cookie 的瀏覽器中，訪客在次要網站和主要網站上仍會識別為不同身分。

**為何 Experience Cloud ID (MID) 參數不在 Analytics 請求中？**

如果 Identity Service 正確傳回資訊，但您未看見 `MID` 參數，請確定您已升級至 AppMeasurement 的支援版本。

**我的網站是否可搭配 Identity Service 使用 H 程式碼和 JavaScript 適用的 AppMeasurement？**

是。只要這兩個檔案參照相同的 VisitorAPI.js 檔案，您就可以在整個網站上混合使用 H 程式碼和適用於 JavaScript 的 AppMeasurement。

但 visitorAPI.js 程式碼 1.6 版或更新版本不支援 H 程式碼。如果您想要升級至 visitorAPI.js 1.6版 (或更新版本)，則無法繼續使用 H 程式碼。

**什麼是寬限期？應如何設定？**

參閱 [ Identity Service 寬期限](../reference/analytics-reference/grace-period.md)並聯絡[客戶服務](https://helpx.adobe.com/tw/marketing-cloud/contact-support.html)。

**為什麼我需要移轉至即時資料蒐集 (RDC) 才能使用 Identity Service？**

RDC 可以提升全域效能，此外為了確保您的實作可針對未來採用 Adobe 頂尖全域網路的功能做好準備，也有需要進行 RDC 移轉。請參閱 [Analytics 需求：地區資料收集 (RDC)](../reference/requirements.md#section-7d04bb013bc84a25bae3b148bc0ca25f)。

## 報告 {#section-123cd55a32e54a45a23beb140becfa8f}

**搭配 Identity Service 使用 Analytics 而造成的不一致，有哪些可能的原因？**

使用 Identity Service 時，發生不一致的常見原因包括:

* 繼續使用舊版 s_vi Cookie。這會造成資料收集不一致。
* 在訪客從意見調查瀏覽至快顯視窗時重複計算訪客數。

## Cookie {#section-b7d5384fbedd47b09e1030211c39a3d1}

**如果 Identity Service 無法設定 AMCV Cookie，Analytics 中會發生什麼事？**

在三種情況下，新訪客的 Analytics 資料可能會受此影響：

1. 終端使用者在 AMCV Cookie 成功設定之前 (在 30 秒逾時範圍內) 離開頁面。

   如果訪客在頁面載入完成前離開頁面，則不會傳送 Analytics 點擊。在此情況下，Analytics 將不會接收資料，且會認定資料因頁面提早關閉而遺失。根據我們的測試 (包含偏遠地理位置)，我們發現平均只有不到 1% 的流量有此情況。需要注意的是，即使未提供 Identity Service，這種情況也會出現；這是將 Analytics 資料收集程式碼包含在頁面底部的一種工具。

1. 由於連接速度緩慢或瀏覽器「旋轉」，終端使用者在 30 秒逾時範圍內未獲得指派 Identity Service 或 Analytics ID。

   Identity Service 和 Analytics ID 均未設定，系統將分配一個用戶端 ID 給訪客。雖然如此即可擷取 Analytics 資料，但若在後續頁面上設定了 Analytics ID，訪客的設定檔將會中斷。用戶端 ID 也不會與任何儲存在 Audience Manager 或 Analytics 中的現有訪客資料相符。如果兩個不同的網域傳送至相同的報告套裝，則此用戶端 ID 也會在 Analytics 中顯示為兩個不同的訪客。

1. 終端使用者在 30 秒逾時範圍內未獲得分配 Identity Service ID，但會獲得分配標準 Analytics 追蹤 ID，而且不會啟用寬限期。

   情況 3 與情況 2 的結果相同，即皆使用基於用戶端的 ID。

>[!TIP]
>
>搭配預設設定使用最新的 VisitorAPI.js 和 AppMeasurement.js 時，應避免上述三種罕見情況所造成的嚴重或明顯影響。

>[!MORELIKETHIS]
>
>* [客戶服務](https://helpx.adobe.com/tw/marketing-cloud/contact-support.html)

