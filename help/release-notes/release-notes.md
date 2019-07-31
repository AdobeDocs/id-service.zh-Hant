---
description: Experience Cloud Identity 服務的功能發佈、更新或變更。
keywords: ID 服務
seo-description: Experience Cloud Identity 服務的功能發佈、更新或變更。
seo-title: 2019 年發行說明
title: 2019 年發行說明
uuid: a5a59410-7f85-48f9-a30a-fef1c2e2b558
translation-type: tm+mt
source-git-commit: 4532d09cc9b4d83fa62c13bd1adac7abdae222b1

---


# 2019 年發行說明 {#release-notes}

Experience Cloud Identity 服務的功能發佈、更新或變更。

## 2019 年發行說明 {#topic-1b9a1c3ec5044e1c987785950f697e25}

[!DNL Experience Cloud] ID 服務的功能發佈、更新或變更。

## 版本 4.4 {#version-4point4}

**新功能**

[SHA256雜湊支援setCustomerIDs](/help/reference/hashing-support.md)。Experience Cloud ID Service(ECID)支援SHA-256雜湊演算法，可讓您傳入客戶ID或電子郵件地址，並傳遞雜湊ID。

**修正、增強功能、改進**

* We made a configuration update to `cookieDomain`. The ECID library now filters out the empty string `cookieDomain` in `initConfig` and uses the top level cookie domain, which is returned by the getDomain method. (CORE - 29223)

* We fixed a bug related to `getVisitorValues` in `localVisitor`. (CORE - 31287)

* We fixed a bug where there was an inconsistency for the MCOPTOUT value in the Safari browser, returned by the `getVisitorValue` method. (CORE - 29719)

* We updated the Opt-in library by adding `optIn.off` to unsubscribe from events.
* We fixed a bug related to the setTimeout function, where `setTimeout` violated the Content Security Policy (CSP) on some customer sites. (CORE - 30623)


## 版本 4.3 {#version-4point3}

**支援ITP2.1**。如果追蹤伺服器設定在第一方CNAME中，則會使用ECID值放置新的Cookie(s_ ecid)。ECID程式庫會參照值，將ID存留超過天。See [ECID library methods in a Safari ITP world](/help/reference/ecid-library-methods.md).

**SecureSecokie config錯誤修正。**

## 版本 4.0 {#section-51a4be943bbe41558f196ef2654513e2}

**選擇加入服務**。選擇加入是 Experience Cloud ID (ECID) 的擴充功能，可讓您控制 Experience Cloud 資料庫是否可以在網頁上建立訪客的 Cookie，以及使用哪個資料庫來執行。Using [Experience Platform Launch](https://docs.adobelaunch.com/), you can simplify gathering visitor opt-in consents for Experience Cloud solution by enabling Analytics, Target, Audience Manager, and other or all select Experience Cloud solutions to opt-in to your consent management system.

## 3.4 版 {#section-046ce29b43af47cc849d4091098f5927}

| 項目 | 說明 |
|---|---|
| 傳入字串時，無法使用 `disableIdSyncs` 標幟。 | 此問題已修正。`getInstance` 函數的 `disableidSyncs` 參數所設定的值現會執行。 |
| 第三方 iFrame 未取得 ECID | 修正 Safari Mobile 上的 ECID 和多種 iFrame 中的 ECID 無法使用的問題。 |

