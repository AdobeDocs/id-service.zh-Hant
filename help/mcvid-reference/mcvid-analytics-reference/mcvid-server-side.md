---
description: 在某些實作中，訪客 ID 會從 JavaScript 傳至伺服器，使伺服器可傳送其他 Analytics 事件 (例如購買)。
keywords: ID 服務
seo-description: 在某些實作中，訪客 ID 會從 JavaScript 傳至伺服器，使伺服器可傳送其他 Analytics 事件 (例如購買)。
seo-title: 混用 JavaScript 的伺服器端實作
title: 混用 JavaScript 的伺服器端實作
uuid: 256ea0e7-1eb4-4c92-9a7e-f61 cb1 ed13 c
translation-type: tm+mt
source-git-commit: bb687c1cd14aae7faef2565dcf9d041a1c06e3bd

---


# 混用 JavaScript 的伺服器端實作 {#server-side-implementation-mixed-with-javascript}

在某些實作中，訪客 ID 會從 JavaScript 傳至伺服器，使伺服器可傳送其他 Analytics 事件 (例如購買)。

ID 服務 API 提供了 [getMarketingCloudVisitorID](../../mcvid-library/mcvid-get-set/mcvid-getmcvid.md) 和 [getAnalyticsVisitorID](../../mcvid-library/mcvid-get-set/mcvid-getanalyticsvisitorid.md) 兩種方法擷取後續可傳至伺服器的 ID 值。

請確實檢查 Experience Cloud 訪客 ID 和 Analytics 訪客 ID 是否存在，並同時傳送這兩個 ID (如果存在)，以確定任何傳送的資料已與現有的 Analytics 訪客設定檔產生關聯。

>[!IMPORTANT]
>
>Java適用的AppMeasurement目前不支援Experience Cloud ID服務。

## 資料插入 API {#section-955ce7664a4646d38b3005cb2df40baf}

在 `<visitorID>` 元素中包含Analytics訪客ID(如果已設定)。

在元素中加入Experience `<marketingCloudVisitorID>` Cloud訪客ID。

請參閱[支援的 XML 標籤](https://marketing.adobe.com/developer/en_US/documentation/data-insertion/r-supported-tags)。

## Java 適用的 AppMeasurement {#section-d664b94934924d048300d9c2b6560085}

適用於 Java 的 AppMeasurement 目前不支援 Experience Cloud ID 服務。
