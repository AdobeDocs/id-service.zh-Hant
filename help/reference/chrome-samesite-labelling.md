---
title: Google Chrome SameSite 標籤異動
description: Adobe ECID (ID 服務) 程式庫文件。
exl-id: f20b25a4-c9bc-41b9-8e49-79b8424e62a0
source-git-commit: ee4b7f8df5766372034da2a76e7acb81ba2a65f0
workflow-type: tm+mt
source-wordcount: '1064'
ht-degree: 96%

---

# Google Chrome SameSite 標籤異動 {#google-chrome-samesite-labelling-changes}

SameSite 屬性會告訴瀏覽器在第一方和第三方情境下觸發 Cookie 的時機和方式。SameSite 屬性可能具有以下任一值：`strict`、`lax` 或 `none`。Chrome、Firefox、Edge、Safari 和 Opera 自 2017 年 11 月起便支援 `strict` 和 `lax`，而 `none` 也已於 2018 年導入。然而，部分舊版瀏覽器並不支援此設定。

2020 年 2 月，Google 發佈 Chrome 80，並將 Cookie 未指定 SameSite 屬性值時的預設設定從 `none` 變更為 `lax`。此設定可防止在第三方情境下使用 Cookie (亦稱為「跨網站」)。之後的第三方 Cookie 都必須設為 `SameSite=none`，並標為 secure。

未指定 SameSite 屬性值的 Cookie 會預設為 `lax`。

如需 SameSite 屬性的詳細資訊，請參閱 [Cookie 標準文件](https://tools.ietf.org/html/draft-ietf-httpbis-rfc6265bis-03#section-4.1)。

## SameSite 屬性值

| SameSite 屬性值 | 說明 |
| ------ | ------------ |
| `strict` | 唯有參考頁面和登陸頁面與 Cookie 所屬的網域相同時，系統才會傳送採用此設定的 Cookie。 |
| `lax` | 唯有瀏覽器 URL 中顯示的網域與 Cookie 的網域相符時，系統才會傳送採用此設定的 Cookie。這是 Chrome 對 Cookie 的新預設值。 |
| `none` | 具有此設定的Cookie可供外部或第三方存取，例如「跨網站」。 此次異動前，Cookie 的預設 SameSite 設定為 `none`，因此使用此設定的話，Cookie 的行為會與其傳統運作方式最為相似。不過，Google 現在要求所有採用此設定的 Cookie 都必須指定安全標幟，亦即 Cookie 只能應要求透過 HTTPS 建立及傳送。Google 會拒絕所有沒有安全標幟的跨網站 Cookie。 |

## Adobe Experience Cloud 客戶須知

**不需更新 JavaScript**

Adobe 產品已發佈伺服器端更新，可使用適當屬性來設定第三方 Cookie。我們的客戶不需自行更新 JavaScript 程式庫。

**確認第三方端點使用 HTTPS**

所有客戶應確認其 JavaScript 設定是使用 HTTPS 來呼叫 Adobe 服務。Target、Audience Manager 和 Experience Cloud Identity Service (ECID) 會將第三方 HTTP 呼叫重新導向各自的 HTTPS 端點，但這麼做可能會增加延遲時間。換句話說，您不需變更設定。Analytics 客戶應更新實作，僅限使用 HTTPS，因為 Analytics 專有的重新導向機制可能會造成資料外洩。

**正確標示的 Cookie 應能順利收集資料**

只要正確標示 Cookie，瀏覽器就不會採取任何動作加以封鎖。消費者可選擇封鎖特定類型的 Cookie，但目前似乎只能使用選擇是否加入的設定來達成此目的。

**忽略未更新標籤的現有第三方 Cookie**

若第三方 Cookie 缺少 SameSite=`none` 和安全標幟，Chrome 80 會忽略在 Chrome 80 開始強制執行這些標幟設定前建立的第三方 Cookie。

許多現有 Adobe 第三方 Cookie 都沒有這些標幟，且必須由 Edge 伺服器更新，用戶才能升級至 Chrome 80，否則這些 Cookie 就會遺失。用戶造訪使用 Cookie 的任何網站時，Edge 伺服器會自動更新。

大部分 Adobe 產品均已為 Cookie 指派適當的標幟。使用第三方資料收集機制，但不使用 ECID 的 Analytics 實作則為例外。客戶的新訪客人數可能會短暫微幅增加，原因在於，原本系統會將這些新訪客視為舊訪客。

**目的地和市集合作夥伴可能的 Cookie 比對減少 (僅限 Audience Manager)**

雖然Adobe可控制其Cookie的更新，但Adobe無法強制合作夥伴進行必要的變更。 若 Audience Manager 客戶使用尚未完成這些更新的目的地或市集合作夥伴，Cookie 比對次數可能會因而減少。

**適合 Analytics 的第三方 Cookie (僅限 Analytics `s_vi` Cookie)**

部分 Analytics 實作會使用 Analytics CNAME 別名，於所在 CNAME 網域中建立 `s_vi` Cookie。如果 CNAME 與您的網站同屬相同網域，系統會將其指定為第一方 Cookie。不過，如果您有多個網域，並在所有網域上使用相同的 CNAME 來收集資料，則系統會將其指定為其他幾個網域的第三方 Cookie。

隨著 `lax` 成為 Chrome 新的預設 SameSite 設定，CNAME 就不會在其他網域中顯示。

為配合此次異動，Analytics 已明確將 `s_vi` Cookie 的 SameSite 值設為 `lax`。若要在適合的第三方情境下使用此 Cookie，請將 SameSite 值設為 `none`，亦即您必須一律使用 HTTPS。請連絡客戶服務人員，為您的安全 CNAME 變更 SameSite 值。

>[!IMPORTANT]
>
>使用 ECID 的 Analytics 客戶、為每個網域使用個別 CNAME 的客戶，或僅使用第三方 Analytics 資料收集的客戶，不必執行此動作。

## Adobe 標準訪客 Cookie

下表僅列出常見訪客標準 Cookie。如需其他 Cookie 設定，請參閱產品專屬文件，或與 Adobe 代表連絡。

### ECID

| Cookie | 類型 | SameSite 屬性 | 安全屬性 |
| ------ | ---- | ------------------ | ---------------- |
| AMCV_###@AdobeOrg | 用戶端第一方 | 未新增值 *Chrome 預設為 `lax` 設定 | 可設定 |
| AMCVS_###@AdobeOrg | 用戶端第一方 | 未新增值 *Chrome 預設為 `lax` 設定 | 可設定 |
| s_ecid | 伺服器端第一方 | SameSite==`lax` | 未設定 |

### Audience Manager

| Cookie | 類型 | SameSite 屬性 | 安全屬性 |
| ------ | ---- | ------------------ | ---------------- |
| Demdex | 第三方 | `none` | 設為 secure |
| Dextp | 第三方 | `none` | 設為 secure |

### Analytics

| Cookie | 類型 | SameSite 屬性 | 安全屬性 |
| ------ | ---- | ------------------ | ---------------- |
| s_vi | <ul><li> 使用 `CNAME` 時為伺服器端第一方 </li> <li>使用 2o7.net 或 omtrdc.net 時為第三方</li></ul> | <ul><li>第一方時為 `lax`</li> <li>第三方時為 `none`</li></ul> *客戶可透過第一方網域的客戶服務工單編輯設定* | 使用 `none` 和 HTTPS 要求時設定 |
| s_fid | 用戶端第一方 | 未新增值 *Chrome 預設為 `lax` 設定 | 未設定 |

### Target

| Cookie | 類型 | SameSite 屬性 | 安全屬性 |
| ------ | ---- | ------------------ | ---------------- |
| mbox | 第一方 | 未新增值 *Chrome 預設為 `lax` 設定 | 未設定 |

### Ad Cloud

| Cookie | 類型 | SameSite 屬性 | 安全屬性 |
| ------ | ---- | ------------------ | ---------------- |
| everest_g_v2 | 第三方 | `none` *僅適用於 Google Chrome 和 Chromium 瀏覽器* | 使用 `none` 和 HTTPS 要求時設定 |
| data_adcloud | 第一方 | 未新增值 *Chrome 預設為 `lax` 設定 | 未設定 |
| ev_tm | 第三方 | `none` *僅適用於 Google Chrome 和 Chromium 瀏覽器* | 使用 `none` 和 HTTPS 要求時設定 |

### Bizible

| Cookie | 類型 | SameSite 屬性 | 安全屬性 |
| ------ | ---- | ------------------ | ---------------- |
| _buid | 第三方 | `none` | Secure |

### Marketo Munchkin

| Cookie | 類型 | SameSite 屬性 | 安全屬性 |
| ------ | ---- | ------------------ | ---------------- |
| _mkto_trk | 用戶端第一方 | 未新增值 *Chrome 預設為 `lax` 設定 | 可針對外部頁面設定 |

>  Adobe 第三方 Cookie 是在伺服器端設定。

如需詳細資訊，請參閱 [Target 的 Google Chrome SameSite 原則](https://experienceleague.adobe.com/docs/target-dev/developer/implementation/privacy/google-chrome-samesite-cookie-policies.html)文件。
