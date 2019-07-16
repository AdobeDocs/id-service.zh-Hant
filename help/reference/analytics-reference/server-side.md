---
description: 在某些實作中，訪客 ID 會從 JavaScript 傳至伺服器，使伺服器可傳送其他 Analytics 事件 (例如購買)。
keywords: ID 服務
seo-description: 在某些實作中，訪客 ID 會從 JavaScript 傳至伺服器，使伺服器可傳送其他 Analytics 事件 (例如購買)。
seo-title: 混用 JavaScript 的伺服器端實作
title: 混用 JavaScript 的伺服器端實作
uuid: 256ea0e7-1eb4-4c92-9a7e-f61cb1ed13c7
translation-type: tm+mt
source-git-commit: 484c52265d8e0b6f0e79cb21d09082fff730a44b

---


# 混用 JavaScript 的伺服器端實作 {#server-side-implementation-mixed-with-javascript}

在某些實作中，訪客 ID 會從 JavaScript 傳至伺服器，使伺服器可傳送其他 Analytics 事件 (例如購買)。

ID 服務 API 提供了 [getMarketingCloudVisitorID](../../library/get-set/getmcvid.md) 和 [getAnalyticsVisitorID](../../library/get-set/getanalyticsvisitorid.md) 兩種方法擷取後續可傳至伺服器的 ID 值。

請確實檢查 Experience Cloud 訪客 ID 和 Analytics 訪客 ID 是否存在，並同時傳送這兩個 ID (如果存在)，以確定任何傳送的資料已與現有的 Analytics 訪客設定檔產生關聯。

>[!IMPORTANT]
>
>Java適用的AppMeasurement目前不支援Experience Platform Identity Service。

## 資料插入 API {#section-955ce7664a4646d38b3005cb2df40baf}

在 `<visitorID>` 元素中加入 Analytics 訪客 ID·(如果已設定)。

在 `<marketingCloudVisitorID>` 元素中加入 Experience Cloud 訪客 ID。

請參閱[支援的 XML 標籤](https://marketing.adobe.com/developer/en_US/documentation/data-insertion/r-supported-tags)。

## Java 適用的 AppMeasurement {#section-d664b94934924d048300d9c2b6560085}

Java適用的AppMeasurement目前並不支援Experience Platform Identity Service。
