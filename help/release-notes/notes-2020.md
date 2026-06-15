---
description: Experience Cloud 身分識別服務的功能發佈、更新或變更。
keywords: ID 服務
title: 2020 年發行說明
exl-id: c9d7876e-debc-4c8e-8ebc-91646610c876
TQID: https://experienceleague.adobe.com/hqAMIyXTeLBPU-4B6AVRXhcWux3bkyViMCrbjoGiRwk
product_v2:
  - id: e1971122-7081-4556-9222-8a31bd71800c
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: f8a45b24-4be7-4f1b-909b-60d06b483a20
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2:
  - id: d3cdead0-685a-4489-9250-4bb709942f66
source-git-commit: 5c41e39a833b527a329f62e5f0929445f47139de
workflow-type: tm+mt
source-wordcount: 216
ht-degree: 91%

---

# Experience Cloud 發行說明 - 2020 {#release-notes}

Experience Cloud 身分識別服務的功能發佈、更新或變更。

## 5.1.1 版

* 修補程式修復以使 VisitorJS 載入到 iFrame 時可使用 `SameSite=None` 設定 AMCV Cookie。

## 5.1.0 版

* 新增 `sameSiteCookie` 設定以指定 `SameSite` 屬性用於 AMCV Cookie。 此設定支援下列 `SameSite` 屬性值：
   * `Strict`
   * `Lax`
   * `None`

如需這些屬性值的詳細資訊，請參閱 [web.dev](https://web.dev/samesite-cookies-explained/) 和 [Chromium 專案的 SameSite 更新](https://www.chromium.org/updates/same-site/)。

## 5.0.1 版

* 修補程式修復以使新的 IAB 同意字串傳送到 Adobe Data Collection 邊緣時可包含 `d_cf` 標幟。

## 5.0.0 版

* Visitor 5.0.0 版，支援 `IAB 2.0`。

## 4.6 版

* 預設為 `loadSSL` 標幟開啟。 所有對身分識別服務的呼叫均預設為透過 `https` 發出。  如果客戶想從 `non-ssl` 頁面透過 http 呼叫身分識別服務，可將其設為 false。
* 更新偵測`Internet-Explorer (IE)`版本的函式，以修正`ESLint`回報的問題。
修正ECID收到選擇加入`pre-approval`且稍後更新時，`Internet-Explorer (IE) 11`上的效能問題。

## 4.5 版

* 從 4.5 版開始，ECID 不允許用戶傳送空 ID 至 `setCustomerIDs` 方法。
* 修正選擇加入功能設為 `doesOptInApply=false` 和 `isIabContext=true` 時發生的問題。

如需查看所有產品每個月的發行說明，請參閱 [Experience Cloud 發行說明](https://experienceleague.adobe.com/docs/release-notes/experience-cloud/current.html?lang=zh-Hant)。

