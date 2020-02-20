---
description: Experience Cloud Identity 服務的功能發佈、更新或變更。
keywords: ID Service
seo-description: Experience Cloud Identity 服務的功能發佈、更新或變更。
seo-title: 2019 年發行說明
title: 2019 年發行說明
uuid: a5a59410-7f85-48f9-a30a-fef1c2e2b558
translation-type: tm+mt
source-git-commit: 25a9af7a28462bc0bd26cf4a5a58203e76a83366

---


# Experience Cloud release notes - 2019 {#release-notes}

Experience Cloud Identity 服務的功能發佈、更新或變更。

## 4.4.1 版

在ECID Launch Extension中新增媒體分析的選擇加入核准前核取方塊(CORE-33185)

**修正**

* ECID啟動擴充功能preOptInApprovals輸入字串剖析問題(CORE-34041)
* 使用trackingServer時的效能下降(CORE-32387)

## 版本 4.4 {#version-4point4}

**新功能**

[setCustomerIDs 的 SHA256 雜湊支援](/help/reference/hashing-support.md)。Experience Cloud ID Service (ECID) 支援 SHA-256 雜湊演算法，可讓您傳入客戶 ID 或電子郵件地址，然後傳出雜湊 ID。

**修正、增強功能、改進項目**

* 我們已對 `cookieDomain` 進行設定上的更新。ECID 程式庫現在會篩選掉 `initConfig` 中的空白字串 `cookieDomain`，並使用由 getDomain 方法傳回的頂層 Cookie 網域。(CORE - 29223)

* 我們已在 `localVisitor` 中修正 `getVisitorValues` 的相關問題。(CORE - 31287)

* 我們已修正 Safari 瀏覽器中，`getVisitorValue` 方法傳回的 MCOTOUT 值不一致的錯誤。(CORE - 29719)

* 我們更新了選擇加入程式庫，新增 `optIn.off` 以取消訂閱事件。
* 我們修正了與 setTimeout 函數相關的錯誤，其中 `setTimeout` 在某些客戶網站上違反了內容安全性原則 (CSP)。(CORE - 30623)


## 版本 4.3 {#version-4point3}

**支援 ITP 2.1**。如果追蹤伺服器設定在第一方 CNAME 中，則會使用 ECID 值放置新的 Cookie (s_ecid)。ECID 程式庫會參照值，將 ID 保留超過 7 天。請參閱 [Safari ITP 領域的 ECID 程式庫方法](/help/reference/ecid-library-methods.md)。

**secureCookie 設定的錯誤修正。**

## 4.1 版

依新 `publishDestinations` API變更更新。 透過此更新，頁面的反向連結資訊可在 ID 同步期間公開 (如有需要)。(CORE - 23693)


## 4.2 版

支援IAB TCF的Audience manager外掛程式，可透過ECID選擇加入物件取得。

**修正**

* IAB + OptIn無法取得MID以重新造訪客戶(CORE-26022)
* 修正DTM(DTM-12958)中選擇加入doesOptInApply組態的錯誤
* ECID選擇退出會停用ID同步(CORE-23814)

## 版本 4.0 {#section-51a4be943bbe41558f196ef2654513e2}

**選擇加入服務**。選擇加入是 Experience Cloud ID (ECID) 的擴充功能，可讓您控制 Experience Cloud 資料庫是否可以在網頁上建立訪客的 Cookie，以及使用哪個資料庫來執行。Using [Experience Platform Launch](https://docs.adobelaunch.com/), you can simplify gathering visitor opt-in consents for Experience Cloud solution by enabling Analytics, Target, Audience Manager, and other or all select Experience Cloud solutions to opt-in to your consent management system.

## 版本 3.4 {#section-046ce29b43af47cc849d4091098f5927}

| 項目 | 說明 |
|---|---|
| 傳入字串時，無法使用 `disableIdSyncs` 標幟。 | 此問題已修正。`getInstance` 函數的 `disableidSyncs` 參數所設定的值現會執行。 |
| 第三方 iFrame 未取得 ECID | 修正 Safari Mobile 上的 ECID 和多種 iFrame 中的 ECID 無法使用的問題。 |
