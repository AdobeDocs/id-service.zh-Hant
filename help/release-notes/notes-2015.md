---
description: 2015 年發行說明和更新。
keywords: ID 服務
seo-description: 2015 年發行說明和更新。
seo-title: 2015 年發行說明
title: 2015 年發行說明
uuid: 49423699-1e0f-49e4-9135-2ae84b4f92df
translation-type: tm+mt
source-git-commit: 50a5b4d3a27fd8b21437f02bd9390565f23ac7e6

---


# 2015 年發行說明 {#release-notes}

2015 年發行說明和更新。

## 1.5.3 版 {#section-7c09ba2832bd4644a1ccc3aa83abe66a}

2015 年 11 月

兒童線上隱私保護法(COPPA)禁止在未經父母明確同意下，在線上收集13歲以下兒童的個人資訊。客戶擔憂 COPPA 會在 [!DNL Experience Cloud] ID 服務程式碼中新增選用變數，使該程式碼無法在第三方瀏覽器網域中設定 Cookie。請參閱 [Experience Platform Identity Service](../reference/coppa.md#concept-d7ddf81bebd74f129661fcec1ca19413)中的COPPA支援。適用於 1.5.3 版或更高版本。

## 版本 1.5.2 {#section-e3c73e47539942a89b02d33061128148}

2015 年 9 月

* 修正 Safari 瀏覽器在使用者封鎖第三方 Cookie 時，功能無法同步服務使其得以運作的問題。(AAM-20764)

* 呼叫ID服務現在會在 `d_visid_ver=` 參數中包含版本ID。傳回 ID 有助於內部團隊疑難排解問題並提供支援。(AAM-20824)

## 1.5.1版 {#section-f4309d7917964a748fee4bdb45bffa44}

2015 年 8 月

* 修正錯誤，防止 ID 服務在沒有可同步或可啟動的資料時請求 iframe。(AAM-20164)
* 修正錯誤，此錯誤會讓 ID 服務無法正常設定多部分頂級網域的 Cookie。例如，如果您有一個類似 `my_company.co.uk` 的網域，在某些情況下，ID 服務只會在 `co.uk` 設定 Cookie。(AN-104683)

   此錯誤只會影響符合下列*所有*條件的部分用戶端：

   * 使用 ID 服務。
   * 已啟用[寬限期](../reference/analytics-reference/grace-period.md)*或*使用第一方 Cookie，且使用者封鎖第三方 Cookie。

   * 擁有的頁面具有多部分的頂級網域。

此版本中的文件修訂包括:

* [API方法和程式碼庫](../library/library.md#concept-ff27497375644a898d47984aefb21c97)：重新整理內容和文字。在大多數情況下，每個方法會有專屬的頁面。
* [Experience Platform Identity Service的需求](../reference/requirements.md)：修訂內容和重新整理的文字。

## 1.5版 {#section-db5edfa11ae143ada07a96e0ab06dc57}

2015 年 7 月

[!DNL Experience Cloud] ID 服務支援多個 ID 與驗證狀態。此變更也移除了對 [!DNL Audience Manager] 函數所用 `setCustomerIDs` DPIP－使用者 ID 對應的過時支援。請參閱 [客戶ID和驗證狀態](../reference/authenticated-state.md)

## 版本 1.4 {#section-f5c596f355b14da28f45c798df513572}

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

## 1.3.5版 {#section-eed4567f058f446d9a819e4682621aed}

2015 年 2 月

修正 AAM Blob 和位置提示之請求逾時的處理。現在，針對逾時，系統會將目前頁面的這些欄位正確地保留空白，並進行所有回呼。逾時會被視為錯誤條件，因此會在下一頁再試一次。(AN-94473、AN-94474)

## 第1.3.4版 {#section-bca4a3e7c05546b7af1c9ec47fdb3331}

2015 年 1 月

重新運作 `<head>/<body>` JSONP請求 `<script>` 標籤容器的標籤尋找， `<script>` 以及建立標籤以考慮不同DOM實作(HTML與XHTML)的不同大小寫區分設定。(AN-9355)
