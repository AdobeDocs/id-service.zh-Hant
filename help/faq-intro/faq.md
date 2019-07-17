---
description: 關於使用 ID 服務的功能、功用和問題之常見問題集。
keywords: ID 服務
seo-description: 關於使用 ID 服務的功能、功用和問題之常見問題集。
seo-title: ID 服務常見問題解答
title: ID 服務常見問題解答
uuid: e8d8f819-3d73-4fa2-864c-4867071c14ee
translation-type: tm+mt
source-git-commit: e6d65f1bfed187d7440512e8f3c2de0550506c95

---


# ID 服務常見問題解答{#id-service-faqs}

關於使用 ID 服務的功能、功用和問題之常見問題集。

## 功能 {#section-659e89f8b9a74cb8afff35587dc96836}

**ID 服務提供哪些功能或功用?**

請參閱[概述](../introduction/overview.md).

**為什麼 ID 服務沒有進行呼叫以擷取 Experience Cloud ID?**

這是個難以診斷的問題。您可以檢查網站的內容安全性原則標題，如果您設有嚴格的的安全性原則，這些設定便可以封鎖 ID 服務進行的第三方呼叫。請參閱[內容安全政策和Experience Cloud Identity Service](../reference/csp.md#concept-968c423a7392479db0a0d821ae9783e3)。

**VisitorAPI.js 檔案儲存**

如果您以本機檔案的方式，在行動應用程式中託管 VisitorAPI.js，可能會發生問題。建議您在網頁伺服器上託管檔案。

## 頁面載入時間與延遲 {#section-c78e148d8dbe4c77a436ef0f2af5434b}

**置入 ID 服務 VisitorAPI.js 程式庫對頁面載入時間有什麼影響?**

將 VisitorAPI.js 程式庫放置在程式碼中 `<head>` 區段的頁面頂端。這可確保在頁面本文載入前向 ID 發出呼叫，同時可大幅提升傳回 ID 的成功率。

ID 服務呼叫為非同步，且只會向 [demdex.net domain](https://marketing.adobe.com/resources/help/en_US/aam/demdex-calls.html) 發出呼叫。ID 服務呼叫不會阻擋其他元素載入頁面。

若是 [!DNL Target] 客戶，在頁面的 `<body>` 放置 ID 服務程式碼可能會增加其成功封鎖 [!DNL Target] 呼叫的機率。如果您必須在頁面本文中放置 ID 服務程式碼，應放置在開放的 `<body>` 標籤後。

**ID 服務會在每次頁面載入時進行伺服器呼叫嗎?**

不會，ID 服務只會在第一次呈現頁面時呼叫，此後會每 7 天呼叫一次。此外，亦不需要伺服器呼叫。ID 服務會在用戶端模式中運作，無需進行伺服器呼叫以傳回 ID。

請參閱[概述](../introduction/overview.md)。

**使用 ID 服務時，造成頁面載入時間緩慢或影響使用者體驗的原因是什麼?**

我們很難一一記載所有可能的情況。數十億的客戶連接至我們的服務，客戶所在的地區以及連線方式各有不同，這些都會影響效能。例如:

* 速度會依行動網路不同而有很大的差異。這些網路則受訊號和資料或語音封包遺失的影響。
* 在各種不同條件下連接至 WiFi 也會影響裝置的連線能力。舉例來說，在咖啡店或機場這類公共場所中，必須透過衛星彈回封包才能到達地面網路，因此封包遺失和速度是這種環境中常見的問題。
* 未曾妥善設定的區域網路，則會影響連線能力和速度。
* 用戶端裝置本身也可能有問題，例如記憶體不足、過多的磁碟切換動作，或是相對於目前工作負載來說有限的 CPU 能力。
* 瀏覽器排入佇列和執行遠端伺服器呼叫，甚至是透過不同規則處理回應，則會依瀏覽器製造商和版本而有所不同。此行為會影響速度和效能。

**您可以舉出一些能縮短頁面載入時間的改善方法嗎?**

例如執行緒禮讓作業。我們推出了執行緒禮讓作業以處理多重 ID 同步請求。我們從實驗室報告中發現，若為執行多重 ID 同步的客戶，由於執行連續 CPU 運算，因此會導致 UI 發生壅塞情況。有鑑於此，我們推出了執行緒禮讓作業，藉此按照每個執行緒 100 毫秒的頻率隔離 ID 同步請求。

這項變革改善了使用 Visitor 2.3.0+ 與 DIL 6.10+ 之客戶的效能。下圖顯示了頁面載入時間的改善情況:

![](assets/id_sync_improvements_copy.png)

**使用 CORS 與 JSON-P 的瀏覽器要求會影響網頁效能嗎?**

相較於透過 JSONP 進行資源要求，透過 CORS 一般成效比較好。相對於頁面上其他同步和非同步呼叫︳若是使用 JSONP，某些瀏覽器會將要求排入佇列並取消優先順序。CORS 有助確保在瀏覽器呼叫堆疊中會將這些要求以高優先順序來處理。

請參閱[Experience Cloud Identity Service](../reference/cors.md#concept-6c280446990d46d88ba9da15d2dcc758)中的CORS支援。

## 安全性 {#section-b176b8492fbe4acfb79ebb30ec902f98}

**ID 服務是否支援 CORS?**

是。See [CORS Support in the Experience Cloud Identity Service](../reference/cors.md#concept-6c280446990d46d88ba9da15d2dcc758).

**什麼是 CORS?**

*`Cross-Origin Resource Sharing`*&#x200B;或 CORS 是瀏覽器用於要求資源的方法。ID 服務一律會在支援 CORS 的瀏覽器中使用 CORS 來要求資源。ID 服務在不支援 CORS 的舊版瀏覽器上會藉由 JSON-P 要求資源。請參閱 [Experience Cloud](../reference/cors.md#concept-6c280446990d46d88ba9da15d2dcc758)。

**如果我有嚴格的安全要求，並且從來不想使用 JSONP，該怎麼做?**

如果您有嚴格的安全要求，請將 ID 服務 API 設定為 `useCORSOnly: true`。請僅在確信您網站訪客使用的瀏覽器都支援 CORS 的情形下，才啟用此模式。

請參閱[Experience Cloud](../reference/cors.md#concept-6c280446990d46d88ba9da15d2dcc758) 及 [useCORSOnly](../library/function-vars/use-cors-only.md#reference-8a9a143d838b48d6b23329b84b13e1fa)。

>[!MORE_LIKE_THIS]
>
>* [客戶服務](https://helpx.adobe.com/marketing-cloud/contact-support.html)

