---
description: 提供 Experience Cloud Identity 服務的功能發佈、更新或變更資訊。
keywords: ID Service
seo-description: 提供 Experience Cloud Identity 服務的功能發佈、更新或變更資訊。
seo-title: 2020 年發行說明
title: 2020 年發行說明
translation-type: tm+mt
source-git-commit: c4da0f3da99a96d2be7421f49e0e88286d0505e0

---


# Experience Cloud 發行說明 - 2020 {#release-notes}

提供 Experience Cloud Identity 服務 (ECID) 的功能發佈、更新或變更資訊。

## 4.6 版

* 預設 `loadSSL` 為開啟標幟。 依預設，所有對Identity Service的呼叫 `https` 都將開啟。  如果客戶想要從其頁面的http上呼叫Identity Services，可將其設為 `non-ssl` false。
* 已更新用來偵測版本 `Internet-Explorer (IE)` 的函式，以修正報告的問題 `ESLint`。
修正ECID獲得選擇加入 `Internet-Explorer (IE) 11` 並稍後更新時 `pre-approval` 的效能問題。

## 4.5 版

* 從 4.5 版開始，ECID 不允許使用者傳送空 ID 至 `setCustomerIDs` 方法。
* Fixed an issue occurring when opt-in is configured as `doesOptInApply=false` and `isIabContext=true`.
