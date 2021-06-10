---
description: 在某些實作中，訪客 ID 會從 JavaScript 傳至伺服器，使伺服器可傳送其他 Analytics 事件 (例如購買)。
keywords: ID 服務
title: 混用 JavaScript 的伺服器端實作
exl-id: 1986ee11-2021-4f34-bb56-6eaa87b6dd6d
source-git-commit: 06e935a4ba4776baa900d3dc91e294c92b873c0f
workflow-type: tm+mt
source-wordcount: '181'
ht-degree: 100%

---

# 混用 JavaScript 的伺服器端實作 {#server-side-implementation-mixed-with-javascript}

在某些實作中，訪客 ID 會從 JavaScript 傳至伺服器，使伺服器可傳送其他 Analytics 事件 (例如購買)。

ID 服務 API 提供 [getMarketingCloudVisitorID](../../library/get-set/getmcvid.md) 和 [getAnalyticsVisitorID](../../library/get-set/getanalyticsvisitorid.md) 方法，用以擷取後續可傳至伺服器的 ID 值。

請確實檢查 Experience Cloud 訪客 ID 和 Analytics 訪客 ID 是否存在，並同時傳送這兩個 ID (如果存在)，以確定任何傳送的資料已與現有的 Analytics 訪客設定檔產生關聯。

>[!IMPORTANT]
>
>適用於 Java 的 AppMeasurement 目前不支援 Experience Cloud Identity Service。

## 資料插入 API {#section-955ce7664a4646d38b3005cb2df40baf}

在 `<visitorID>` 元素中加入 Analytics 訪客 ID·(如果已設定)。

在 `<marketingCloudVisitorID>` 元素中加入 Experience Cloud 訪客 ID。

請參閱[支援的 XML 標籤](https://www.adobe.io)。

## Java 適用的 AppMeasurement {#section-d664b94934924d048300d9c2b6560085}

適用於 Java 的 AppMeasurement 目前不支援 Experience Cloud Identity Service。
