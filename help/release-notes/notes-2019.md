---
description: 提供 Experience Cloud Identity 服務的功能發佈、更新或變更資訊。
keywords: ID 服務
seo-description: Experience Cloud Identity 服務的功能發佈、更新或變更。
seo-title: 2019 年版本注意事項
title: 2019 年版本注意事項
uuid: a5a59410-7f85-48f9-a30a-fef1c2e2b558
exl-id: 11439e27-9740-4afc-a2b8-5e35d179f34f
translation-type: ht
source-git-commit: 4453ebf701ea2dc06e6093dd77be6eb0f3b2936e
workflow-type: ht
source-wordcount: '424'
ht-degree: 100%

---

# Experience Cloud 版本注意事項 - 2019 {#release-notes}

提供 Experience Cloud Identity 服務的功能發佈、更新或變更資訊。

## 4.4.1 版

在 ECID Launch Extension 中新增媒體分析在核准加入服務前的核取方塊。

**修正**

* ECID 啟動擴充功能 preOptInApprovals 輸入字串剖析問題。
* 使用 trackingServer 時效能下降。

## 版本 4.4 {#version-4point4}

**新功能**

[setCustomerIDs 的 SHA256 雜湊支援](/help/reference/hashing-support.md)。Experience Cloud ID Service (ECID) 支援 SHA-256 雜湊演算法，可讓您傳入客戶 ID 或電子郵件地址，然後傳出雜湊 ID。

**修正、增強功能、改進項目**

* 我們已對 `cookieDomain` 進行設定上的更新。ECID 程式庫現在會篩選掉 `initConfig` 中的空白字串 `cookieDomain`，並使用由 getDomain 方法傳回的頂層 Cookie 網域。
* 我們已在 `getVisitorValues` 中修正 `localVisitor` 的相關問題。
* 我們已修正 Safari 瀏覽器中，`getVisitorValue` 方法傳回的 MCOTOUT 值不一致的錯誤。
* 我們更新了選擇加入程式庫，新增 `optIn.off` 以取消訂閱事件。
* 我們修正了與 setTimeout 函數相關的錯誤，其中 `setTimeout` 在某些客戶網站上違反了內容安全性原則 (CSP)。

## 版本 4.3 {#version-4point3}

**支援 ITP 2.1**。如果追蹤伺服器設定在第一方 CNAME 中，則會使用 ECID 值放置新的 Cookie (s_ecid)。ECID 程式庫會參照值，將 ID 保留超過 7 天。請參閱 [Safari ITP 領域的 ECID 程式庫方法](/help/reference/ecid-library-methods.md)。

**secureCookie 設定的錯誤修正。**

## 4.1 版

依據新 `publishDestinations` API 變更更新。透過此更新，頁面的反向連結資訊可在 ID 同步期間公開 (如有需要)。

## 4.2 版

支援適用於 IAB TCF 的 Audience Manager 增效模組，這可透過 ECID 選擇加入物件取得。

**修正**

* IAB + OptIn 無法取得 MID 以重新造訪客戶。
* 修正 DTM 中選擇加入 doesOptInApply 組態的錯誤。
* ECID 選擇退出會停用 ID 同步功能。

## 版本 4.0 {#section-51a4be943bbe41558f196ef2654513e2}

**選擇加入服務**。選擇加入是 Experience Cloud ID (ECID) 的擴充功能，可讓您控制 Experience Cloud 程式庫是否可以在網頁上建立訪客的 Cookie，以及使用哪個程式庫來執行。您可以使用 [Experience Platform Launch](https://docs.adobelaunch.com/)，讓 Analytics、Target、Audience Manager 及其他或所有指定 Experience Cloud 解決方案選擇加入您的同意管理系統，簡化 Experience Cloud 解決方案收集訪客是否同意選擇加入的程序。

## 版本 3.4 {#section-046ce29b43af47cc849d4091098f5927}

| 項目 | 說明 |
|---|---|
| 傳入字串時，無法使用 `disableIdSyncs` 標幟。 | 此問題已修正。`getInstance` 函數的 `disableidSyncs` 參數所設定的值現會執行。 |
| 協力廠商 iFrames 未取得 ECID | 修正 Safari Mobil 和不同 iFrames 上 ECID 無法運作的問題。 |
