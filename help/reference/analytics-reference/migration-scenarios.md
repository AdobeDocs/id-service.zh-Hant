---
description: 包含伺服器範例設定和必要的移轉步驟。
keywords: ID 服務
title: Experience Cloud Identity 服務移轉案例
exl-id: 419532bf-399f-4646-a95f-31c35535d6fc
source-git-commit: 06e935a4ba4776baa900d3dc91e294c92b873c0f
workflow-type: tm+mt
source-wordcount: '380'
ht-degree: 100%

---

# Experience Cloud Identity 服務移轉案例 {#experience-cloud-id-service-migration-scenarios}

包含伺服器範例設定和必要的移轉步驟。

## 單一 Web 屬性 {#section-6ccfea84628d46c99507cb124e7f5445}

* **客戶**：範例 Company Inc.
* **已啟用 Experience Cloud**：否
* **Web 屬性**：example.com
* **資料收集伺服器**：metrics.example.com、smetrics.example.com
* **Analytics JavaScript 檔案**：適用於所有網站頁面的單一檔案

首先，客戶應該啟用 Experience Cloud (請參閱 [要求](../../reference/requirements.md))。此外，由於它們有單一 JavaScript 檔案，所以該客戶不需要寬限期。該客戶也將設定訪客移轉，然後從其資料收集 CNAME 移轉到別處 (這不是必要操作)。

## 多個 JavaScript 檔案、硬式編碼影像標籤 {#section-a665f6ee202940449198e4e7a5dcac54}

* **客戶**：其他範例 Company Inc.
* **已啟用 Experience Cloud**：是
* **Web 屬性**：anotherexample.com
* **資料收集伺服器**：anotherexampleco.112.2o7.net
* **Analytics JavaScript 檔案**：多個 JavaScript 檔案。一個檔案適用於他們的主要網站，另一個檔案適用於其在不同 CMS 中維護的支援區段。
* **其他資料收集方法**：一個網站區段上的硬式編碼影像標籤

首先，客戶應該尋找其 Adobe Experience Cloud 組織 ID (請參閱 [要求](../../reference/requirements.md))。接著，他們應該設定移轉寬限期，因為他們使用多個 JavaScript 檔案。此客戶也將設定訪客移轉，然後從 `*.2o7.net` 移轉至 `*.sc.omtrdc.net`。

當此客戶更新至最新的 Analytics JavaScript 程式碼以準備開始使用 [!DNL Experience Cloud] ID 服務時，他們也將更新所有的硬式編碼影像標籤，以改用 JavaScript。

## 多個 Web 屬性、多個 JavaScript 檔案和 Flash 型影片播放程式 {#section-34647995ff3740b999fdee22d885e515}

* **客戶**：有效的客戶 LLC
* **已啟用 Experience Cloud**：是
* **Web 屬性**：mymainsite.com、myothersiteA.com、myothersiteB.com
* **資料收集伺服器**：metrics.mymainsite.com、smetrics.mymainsite.com
* **Analytics JavaScript 檔案**：多個 JavaScript 檔案。每個 Web 屬性使用一個檔案。
* **其他資料收集方法**：Flash 型影片播放程式

首先，客戶應該尋找其 Adobe Experience Cloud 組織 ID (請參閱 [要求](../../reference/requirements.md))。接著，他們應該設定移轉寬限期，因為他們使用多個 JavaScript 檔案。該客戶會追蹤其主要網域與子網域之間的訪客，好讓他們可以繼續搭配訪客 ID 服務使用其資料收集 CNAME。

當此客戶更新至最新的 Analytics JavaScript 程式碼以準備開始使用 [!DNL Experience Cloud] ID 服務時，他們也會將 Flash 型影片播放程式更新為最新版的「Flash 適用的 AppMeasurement」。
