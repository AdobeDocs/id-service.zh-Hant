---
description: 2015 年版本注意事項和更新。
keywords: ID 服務
title: 2015 年版本注意事項
exl-id: 57c45726-f856-4af5-a30a-9a1bdcaa6411
source-git-commit: 06e935a4ba4776baa900d3dc91e294c92b873c0f
workflow-type: tm+mt
source-wordcount: '408'
ht-degree: 100%

---

# 2015 年版本注意事項 {#release-notes}

2015 年版本注意事項和更新。

## 1.5.3 版 {#section-7c09ba2832bd4644a1ccc3aa83abe66a}

2015 年 11 月

兒童網路隱私保護法 (COPPA) 禁止在未經父母明確同意下，透過網路收集 13 歲以下兒童的個人資訊。客戶擔憂 COPPA 會在 [!DNL Experience Cloud] ID 服務程式碼中新增選用變數，使該程式碼無法在第三方瀏覽器網域中設定 Cookie。請參閱 [Experience Cloud Identity 服務的 COPPA 支援](../reference/coppa.md#concept-d7ddf81bebd74f129661fcec1ca19413)。適用於 1.5.3 版或更高版本。

## 1.5.2 版 {#section-e3c73e47539942a89b02d33061128148}

2015 年 9 月

* 已修正 Safari 瀏覽器中的一個錯誤，該錯誤導致同步服務在用戶已封鎖第三方 Cookie 時無法運作。(AAM-20764)

* 對 ID 服務發出的呼叫現在也在 `d_visid_ver=` 參數中納入版本 ID。傳回的 ID 可幫助內部團隊進行疑難排解及提供支援。(AAM-20824)


## 1.5.1 版 {#section-f4309d7917964a748fee4bdb45bffa44}

2015 年 8 月

* 已修正一個錯誤，該錯誤導致 ID 服務在沒有資料可同步或引發時無法要求 iframe。(AAM-20164)
* 已修正一個錯誤，該錯誤導致 ID 服務無法正常設定多部分、最上層網域的 Cookie。例如，如果您有一個類似 `my_company.co.uk` 的網域，在某些情況下，ID 服務只會在 `co.uk` 設定 Cookie。(AN-104683)

   此錯誤只會影響符合下列&#x200B;*所有*&#x200B;條件的部分用戶端:

   * 使用 ID 服務。
   * 已啟用[寬限期&#x200B;](../reference/analytics-reference/grace-period.md)*或*&#x200B;使用第一方 Cookie，且用戶封鎖第三方 Cookie。

   * 擁有的頁面具有多部分、最上層網域。

這個版本的文件修訂包括：

* [API 方法與程式碼程式庫](../library/library.md#concept-ff27497375644a898d47984aefb21c97)：重新整理內容與文字。在大多數情況下，每個方法會有專屬的頁面。
* [Experience Cloud Identity 服務的需求](../reference/requirements.md)：修訂內容與重新整理文字。

## 1.5 版 {#section-db5edfa11ae143ada07a96e0ab06dc57}

2015 年 7 月

[!DNL Experience Cloud] ID 服務支援多個 ID 與驗證狀態。此變更也移除了對 [!DNL Audience Manager] 函數所用 `setCustomerIDs` DPIP－用戶 ID 對應的過時支援。請參閱[客戶 ID 與驗證狀態](../reference/authenticated-state.md)

## 1.4 版 {#section-f5c596f355b14da28f45c798df513572}

2015 年 5 月

和 1.4 版相同，設定組態的偏好方法，是將組態物件 (作為第二參數) 傳遞至 `Visitor.getInstance` 函數。

```js
var visitor = Visitor.getInstance("016D5C175213CCA80A490D05@AdobeOrg",{ 
    "loadTimeout":1000, 
    "trackingServer":"myco.sc.omtrdc.net", 
    "idSyncContainerID":80 
});
```

請參閱 [Experience Cloud](../implementation-guides/setup-analytics.md#concept-9ebbea85cb844a15b557be572cd142fd)。

## 1.3.5 版 {#section-eed4567f058f446d9a819e4682621aed}

2015 年 2 月

已修正 AAM Blob 和位置提示要求的逾時處理。現在發生逾時時，系統會正確地將目前頁面的這些欄位留白，並發出所有回呼。逾時會被視為錯誤狀況，所以它將在下一頁重試。(AN-94473、AN-94474)

## 1.3.4 版 {#section-bca4a3e7c05546b7af1c9ec47fdb3331}

2015 年 1 月

修訂 JSONP 要求 `<head>/<body>` 標籤容器的 `<script>` 標籤搜尋及 `<script>` 標籤建立作業，以處理不同 DOM 實作 (HTML 與 XHTML) 的不同區分大小寫設定。(AN-9355)
