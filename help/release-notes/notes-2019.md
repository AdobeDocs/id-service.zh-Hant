---
description: Experience Cloud 身分識別服務的功能發佈、更新或變更。
keywords: ID 服務
title: 2019 年發行說明
exl-id: 11439e27-9740-4afc-a2b8-5e35d179f34f
TQID: https://experienceleague.adobe.com/KnO04dnP6z7gKrr8vkFiiToDSBfClpiOJkGq8949ahA
product_v2:
  - id: e1971122-7081-4556-9222-8a31bd71800c
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: f8a45b24-4be7-4f1b-909b-60d06b483a20
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2:
  - id: d095671a-1355-40aa-8b5f-06c33c68080b
source-git-commit: 5c41e39a833b527a329f62e5f0929445f47139de
workflow-type: tm+mt
source-wordcount: 438
ht-degree: 100%

---

# Experience Cloud 發行說明 - 2019 {#release-notes}

Experience Cloud 身分識別服務的功能發佈、更新或變更。

## 4.4.1 版

在 ECID Launch Extension 中新增媒體分析在核准加入服務前的核取方塊。

**修正**

* ECID 啟動擴充功能 preOptInApprovals 輸入字串剖析問題。
* 使用 trackingServer 時效能下降。

## 4.4 版 {#version-4point4}

**新功能**

[setCustomerIDs 的 SHA256 雜湊支援](/help/reference/hashing-support.md)。 Experience Cloud ID Service (ECID) 支援 SHA-256 雜湊演算法，可讓您傳入客戶 ID 或電子郵件地址，然後傳出雜湊 ID。

**修正、增強功能、改進項目**

* 我們已對 `cookieDomain` 進行設定上的更新。 ECID 程式庫現在會篩選掉 `initConfig` 中的空白字串 `cookieDomain`，並使用由 getDomain 方法傳回的頂層 Cookie 網域。
* 我們已在 `getVisitorValues` 中修正 `localVisitor` 的相關錯誤。
* 我們已修正 Safari 瀏覽器中，`getVisitorValue` 方法傳回的 MCOTOUT 值不一致的錯誤。
* 我們更新了選擇加入程式庫，新增 `optIn.off` 以取消訂閱事件。
* 我們修正了與 setTimeout 函數相關的錯誤，其中 `setTimeout` 在某些客戶網站上違反了內容安全性原則 (CSP)。

## 4.3 版 {#version-4point3}

**支援 ITP 2.1**。 如果追蹤伺服器設定在第一方 CNAME 中，則會使用 ECID 值放置新的 Cookie (s_ecid)。 ECID 程式庫會參照值，將 ID 保留超過 7 天。 請參閱 [Safari ITP 領域的 ECID 程式庫方法](/help/reference/ecid-library-methods.md)。

**secureCookie 設定的錯誤修正。**

## 4.1 版

依據新 `publishDestinations` API 變更更新。 透過此更新，頁面的反向連結資訊可在 ID 同步期間公開 (如有需要)。

## 4.2 版

支援適用於 IAB TCF 的 Audience Manager 增效模組，這可透過 ECID 選擇加入物件取得。

**修正**

* IAB + OptIn 無法取得 MID 以重新造訪客戶。
* 修正 DTM 中選擇加入 doesOptInApply 組態的錯誤。
* ECID 選擇退出會停用 ID 同步功能。

## 4.0 版 {#section-51a4be943bbe41558f196ef2654513e2}

**選擇加入服務**。 選擇加入是 Experience Cloud ID (ECID) 的擴充功能，可讓您控制 Experience Cloud 程式庫是否可以在網頁上建立訪客的 Cookie，以及使用哪個程式庫來執行。 您可以使用 [Experience Platform Launch](https://experienceleague.adobe.com/docs/experience-platform/tags/home.html)，讓 Analytics、Target、Audience Manager 及其他或所有指定 Experience Cloud 解決方案選擇加入您的同意管理系統，簡化 Experience Cloud 解決方案收集訪客是否同意選擇加入的程序。

## 3.4 版 {#section-046ce29b43af47cc849d4091098f5927}

| 項目 | 說明 |
|---|---|
| 傳入字串時，無法使用 `disableIdSyncs` 標幟。 | 此問題已修正。 `getInstance` 函數的 `disableidSyncs` 參數所設定的值現會執行。 |
| 第三方 iFrames 未取得 ECID | 修正 Safari Mobil 和不同 iFrames 上 ECID 無法運作的問題。 |

