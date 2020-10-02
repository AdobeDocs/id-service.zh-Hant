---
title: Google Chrome SameSite標籤變更
seo-title: Google Chrome SameSite標籤變更
description: Adobe ECID (ID 服務) 程式庫的文件。
seo-description: Adobe ECID (ID 服務) 程式庫的文件。
translation-type: tm+mt
source-git-commit: 592ca6ca6a72e57b728e286d0b730c5bd93c0c7b
workflow-type: tm+mt
source-wordcount: '1079'
ht-degree: 4%

---


# Google Chrome SameSite標籤變更 {#google-chrome-samesite-labelling-changes}

SameSite屬性會告訴瀏覽器在第一方和第三方案例中何時及如何觸發Cookie。 SameSite屬性可以有三個值之一： `strict`、 `lax`或 `none`。 Chrome、Firefox、Edge、Safari和Opera自2017年11月推出 `strict` 以 `lax` 來都提供 `none` 支援。 不過，有些舊版瀏覽器不支援此設定。

在2020年2月，Google發行Chrome 80，並將預設設定從 `none` Cookie `lax` 沒有指定的SameSite屬性值時變更為。 此設定可防止在協力廠商內容（亦稱為「跨網站」）中使用Cookie。 隨後產生的任何第三方Cookie都必須設 `SameSite=none` 定為安全。

沒有指定SameSite屬性值的Cookie預設為 `lax`。

請造訪 [Cookie標準檔案](https://tools.ietf.org/html/draft-ietf-httpbis-rfc6265bis-03#section-4.1) ，以取得SameSite屬性的詳細資訊。

## SameSite屬性值

| SameSite屬性值 | 說明 |
| ------ | ------------ |
| `strict` | 只有當反向連結頁面和登陸頁面都屬於Cookie的相同網域時，才會傳送具有此設定的Cookie。 |
| `lax` | 只有當瀏覽器URL中顯示的網域符合Cookie的網域時，才會傳送具有此設定的Cookie。 這是Chrome中Cookie的新預設值。 |
| `none` | 具有此設定的Cookie可供外部或第三方存取，例如「跨網站」。 在進行此變更之前， `none` 是Cookie的預設SameSite設定，因此使用此設定會使Cookie的行為方式與其傳統運作方式最類似。 不過，Google現在要求任何具有此設定的Cookie都必須指定安全標幟，這表示Cookie只會透過HTTPS建立並隨請求傳送。 所有不含安全標幟的跨網站Cookie都會被Google拒絕。 |

## 身為Adobe Experience Cloud客戶，您需要瞭解的

**不需要JavaScript更新**

Adobe產品已發佈伺服器端更新，以設定具有適當屬性的第三方Cookie。 我們的客戶不需要JavaScript程式庫更新。

**確保協力廠商端點使用HTTPS**

所有客戶應確認其JavaScript設定是使用HTTPS來呼叫Adobe服務。 Target、Audience Manager和Experience Cloud Identity Service(ECID)會將協力廠商HTTP呼叫重新導向至其各自的HTTPS端點，以增加延遲。 這表示您不需要變更設定。 Analytics客戶應更新其實作，以便獨佔使用HTTPS，因為Analytics專屬的重新導向可能會造成資料遺失。

**正確標示的Cookie應如預期收集資料**

只要Cookie已正確標示，瀏覽器就不會採取任何動作來封鎖它們。 消費者可以選擇封鎖特定類型的Cookie，但目前這似乎只是選擇加入設定。

**沒有更新標籤的現有第三方Cookie將被忽略**

在Chrome 80開始實施SameSite=之前建立的協力廠商Cookie`none` ，如果這些標幟不存在，Chrome 80將會忽略安全標幟設定。

許多現有的Adobe協力廠商Cookie都沒有這些標幟，而且需要由Edge伺服器更新，使用者才能升級至Chrome 80，否則這些Cookie將會遺失。 當使用者造訪使用Cookie的任何網站時，Edge伺服器會自動更新。

大部分的Adobe產品都已指派適當的標幟給Cookie。 但Analytics實作中，使用協力廠商資料收集且不使用ECID的情況除外。 客戶可能會遇到新訪客數量小幅度的暫時增加，否則將會回訪訪客。

**目的地和市集合作夥伴可能的Cookie比對減少（僅限Audience Manager）**

雖然Adobe可控制Cookie的更新，但Adobe無法強制合作夥伴進行必要的變更。 使用目標合作夥伴或尚未進行這些更新之市場合作夥伴的Audience Manager客戶，Cookie比對可能會減少。

**Analytics好記的協力廠商Cookie(僅限Analytics`s_vi`Cookie)**

有些Analytics實作會使用Analytics CNAME別名，以啟用在 `s_vi` 該CNAME的網域中建立Cookie。 如果CNAME與您的網站位於相同的網域，則會將其指定為第一方Cookie。 不過，如果您擁有多個網域，並在所有網域間使用相同的CNAME進行資料收集，則會將其指定為這些其他網域上的第三方Cookie。

隨著 `lax` 成為Chrome中新的預設SameSite設定，CNAME在其他網域中將不再顯示。

為配合變更，Analytics現在已明確將Cookie的SameSite值設 `s_vi` 定為 `lax`。 若要在友好的協力廠商內容中使用此Cookie，請將SameSite值設為 `none`，這也表示您必須一律使用HTTPS。 請連絡客戶服務，變更您的安全CNAME的SameSite值。

>[!IMPORTANT]
>
>使用ECID的Analytics客戶、對每個網域使用個別CNAME的客戶，或僅使用第三方Analytics資料收集的客戶，不需執行此動作。

## Adobe Standard訪客Cookie

下表僅列出一般訪客標準Cookie。 如需其他Cookie設定，請參閱產品特定檔案或與Adobe代表聯絡。

### ECID

| Cookie | 類型 | SameSite屬性 | 安全屬性 |
| ------ | ---- | ------------------ | ---------------- |
| AMCV_###@AdobeOrg | 用戶端第一方 | 無增值*Chrome預設值為設 `lax` 定 | 可設定 |
| AMCVS_###@AdobeOrg | 用戶端第一方 | 無增值*Chrome預設值為設 `lax` 定 | 可設定 |
| s_ecid | 伺服器端第一方 | SameSite==`lax` | 未設定 |

### Audience Manager

| Cookie | 類型 | SameSite屬性 | 安全屬性 |
| ------ | ---- | ------------------ | ---------------- |
| Demdex | 第三方 | `none` | 設為安全 |
| Dextp | 第三方 | `none` | 設為安全 |

### Analytics

| Cookie | 類型 | SameSite屬性 | 安全屬性 |
| ------ | ---- | ------------------ | ---------------- |
| s_vi | <ul><li> 伺服器端第一方(若使用 `CNAME` </li> <li>使用2o7.net或omtrdc.net時的第三方</li></ul> | <ul><li>`lax` if first-party</li> <li>`none` if third party</li></ul> *客戶可以透過第一方網域的客戶服務票證編輯設定* | 設定，如果使用和 `none` HTTPS要求 |
| s_fid | 用戶端第一方 | 無新增值*Chrome預設值為設 `lax` 定 | 未設定 |

### Target

| Cookie | 類型 | SameSite屬性 | 安全屬性 |
| ------ | ---- | ------------------ | ---------------- |
| mbox | 第一方 | 無增值*Chrome預設值為設 `lax` 定 | 未設定 |

### Ad Cloud

| Cookie | 類型 | SameSite屬性 | 安全屬性 |
| ------ | ---- | ------------------ | ---------------- |
| everest_g_v2 | 第三方 | `none` *僅適用於Google Chrome和Chromium瀏覽器* | 設定，如果使用和 `none` HTTPS要求 |
| data_adcloud | 第一方 | 無增值*Chrome預設值為設 `lax` 定 | 未設定 |
| ev_tm | 第三方 | `none` *僅適用於Google Chrome和Chromium瀏覽器* | 設定，如果使用和 `none` HTTPS要求 |

### Bizible

| Cookie | 類型 | SameSite屬性 | 安全屬性 |
| ------ | ---- | ------------------ | ---------------- |
| _buid | 第三方 | `none` | Secure |

### 馬克托·蒙奇金

| Cookie | 類型 | SameSite屬性 | 安全屬性 |
| ------ | ---- | ------------------ | ---------------- |
| _mkto_trk | 用戶端第一方 | 無增值*Chrome預設值為設 `lax` 定 | 可針對外部頁面進行設定 |

> !![IMPORTANT] Adobe協力廠商Cookie是在伺服器端

如需詳細資訊，請參閱 [Target Google Chrome SameSite政策上的檔案](https://docs.adobe.com/content/help/en/target/using/implement-target/before-implement/privacy/google-chrome-samesite-cookie-policies.html)。