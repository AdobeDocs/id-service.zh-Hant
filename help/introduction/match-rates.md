---
description: 概述 Experience Cloud Identity 服務 (包括 Adobe Media Optimizer 和 ID 服務) 中的 ID 同步程序與匹配率。
keywords: ID Service
seo-description: 概述 Experience Cloud Identity 服務 (包括 Adobe Media Optimizer 和 ID 服務) 中的 ID 同步程序與匹配率。
seo-title: 瞭解 ID 同步和匹配率
title: 瞭解 ID 同步和匹配率
uuid: 31bd655f-2b9e-4f8d-9a1f-e81a6110eda8
translation-type: tm+mt
source-git-commit: d2bc0e7fedc4e48d51f5dad158f9f8bfcb0cb4f3

---


# 瞭解 ID 同步和匹配率{#understanding-id-synchronization-and-match-rates}

概述 Experience Cloud Identity 服務 (包括 Adobe Media Optimizer 和 ID 服務) 中的 ID 同步程序與匹配率。

## ID 同步和匹配率 {#section-f652aae7234945e89d26dd833c5215fb}

ID同步會將ID服務指派的ID與客戶指派給網站訪客的ID相符。 例如，假設ID服務已指派訪客ID 1234。 另一個平台以ID 4321瞭解此訪客。 ID服務在同步過程中將這些ID映射在一起。 結果會新增資料點至客戶對其網站訪客的瞭解。 而且，如果ID服務不符合ID，則會建立新的ID，並使用該ID進行日後同步。

比對比率測量並驗證ID同步程式的有效性。 高匹配率表明，與低匹配率的服務相比，特定服務將更有效率，並提供更廣的線上觀眾。 比較比對率是可量化的方式，可評估不同的整合廣告技術平台。

![](assets/idsync2.png)

**確保高匹配率**

若想產生高匹配率，請務必正確設定 ID 服務 (請參閱[標準實作指南](../implementation-guides/standard.md#concept-89cd0199a9634fc48644f2d61e3d2445))。正確的實作能夠確保高匹配率，因為可讓 ID 服務設定其運作所需的 Cookie，並將 ID 與已啟用的資料合作夥伴進行同步。但是，網際網路連線緩慢、從行動裝置或無線網路收集資料等因素可能會影響ID服務收集、同步及符合ID的效能。 這些用戶端變數不在 ID 服務或 [!DNL Adobe] 的控制範圍之內。

## 描述的 ID 同步程序 {#section-a541a85cbbc74f5682824b1a2ee2a657}

ID服務會即時同步ID。 此程式可在瀏覽器中運作，而非透過伺服器到伺服器的資料傳輸。 下表說明了ID同步過程中的步驟。

**步驟 1: 載入頁面**

訪客造訪您的網站並載入頁面時，`Visitor.getInstance` 函數會向 ID 服務發出 [CORS](../reference/cors.md#concept-6c280446990d46d88ba9da15d2dcc758) 或 JSON-P 呼叫。ID 服務使用 Cookie 回應，其中包含訪客的 [!DNL Experience Cloud] ID (MID)。MID 是指派給每個網站訪客的唯一 ID。另請參閱 [Cookie 與 Experience Cloud Identity 服務](../introduction/cookies.md)。

**步驟2: 載入iFrame**

載入頁面內文時，ID服務會載入名為的iFrame *`Destination Publishing iFrame`*。 The [!UICONTROL Destination Publishing iFrame] loads in a domain separate from the parent page. 此設計有助於確保頁面效能並改善安全性，因為iFrame:

* 相對於父頁面非同步載入。 This means the parent page can load independently from the [!UICONTROL Destination Publishing iFrame]. 從iFrame載入iFrame和載入ID同步像素不會影響父頁面或使用者體驗。
* 盡可能快速載入。 如果速度太快，您可以在視窗載入事件（不建議）之後載入iFrame。 See [idSyncAttachIframeOnWindowLoad](../library/function-vars/idsyncattachiframeonwindowload.md#reference-b86b7112e0814a4c82c4e24c158508f4) for details.
* 防止iFrame中的程式碼存取或影響上層頁面。

See also, [How the Experience Cloud Identity Service Requests and Sets IDs...](../introduction/id-request.md#concept-2caacebb1d244402816760e9b8bcef6a).

**步驟3: Fire ID同步**

ID同步是在「目標發佈iFrame」中引發的URL。 如以下通用範例所示，ID 同步 URL 包含合作夥伴的 ID 同步端點以及重新導向 URL，這會重新導向回包含其 ID 的 [!DNL Adobe]。

`http://abc.com?partner_id=abc&sync_id=123&redir=http://dpm.demdex.net/ibs:dpid=<ADOBE_PARTNER_ID>&dpuuid=<PARTNER_UUID>`

另請參閱[連入資料傳輸的 ID 同步](https://docs.adobe.com/content/help/zh-Hant/audience-manager/user-guide/implementation-integration-guides/sending-audience-data/batch-data-transfer-process/id-sync-http.html)。

**步驟 4: 儲存 ID**

Synchronized IDs are stored on the [edge and core data servers](https://docs.adobe.com/content/help/en/audience-manager/user-guide/reference/system-components/components-edge.html).

## 同步服務負責管理 ID 同步作業 {#section-cd5784d7ad404a24aa28ad4816a0119a}

*`Sync Services`*&#x200B;一詞指的是負責 ID 同步作業的內部 [!DNL Experience Cloud] 技術。此服務預設為啟用。 若要停用此變數，請新增 [選用變數](../library/function-vars/disableidsync.md#reference-589d6b489ac64eddb5a7ff758945e414) 至ID服務 `Visitor.getInstance` 函式。 同步服務可以匹配不同的 [!DNL Experience Cloud] ID，例如:

* 第三方 [!DNL Experience Cloud] Cookie ID 和第一方 [!DNL Experience Cloud] ID。

* 第一方 [!DNL Experience Cloud] Cookie ID 和 [!DNL Adobe Media Optimizer] (AMO) ID。

* 第三方 [!DNL Experience Cloud] Cookie ID 和第三方資料提供者與鎖定平台 ID。這包括資料提供者、需求及/或供應方平台、廣告網路、交換等服務和平台。
* 第一方 [!DNL Experience Cloud] Cookie ID 和跨裝置合作夥伴 ID。

## 與Adobe Advertising Cloud的ID同步化 {#section-642c885ea65d45ffb761f78838735016}

[!DNL Adobe Advertising Cloud] (先前稱 [!DNL Adobe Media Optimizer]為)是iFrame ID同步程式的例外。 由於 [!DNL Advertising Cloud] 是值得信賴的網域，ID 同步會從上層頁面進行，而非 [!UICONTROL Destination Publishing iFrame]。同步期間，ID 服務會在 [!DNL Advertising Cloud] 呼叫 `cm.eversttech.net`，這是 [!DNL Advertising Cloud] 在 Adobe 收購前所使用的舊版網域名稱。將資料傳送至 [!DNL Advertising Cloud] 有助於改善匹配率，而且這是使用 2.0 版 (或更新版本) 的 ID 服務之客戶的專屬自動功能。另請參閱 [Advertising Cloud Cookie](https://docs.adobe.com/content/help/en/core-services/interface/ec-cookies/cookies-advertising-cloud.html)。

>[!MORELIKETHIS]
>
>* [瞭解傳至 Demdex 網域的呼叫](https://docs.adobe.com/content/help/zh-Hant/audience-manager/user-guide/reference/demdex-calls.html)

