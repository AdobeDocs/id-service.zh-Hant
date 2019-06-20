---
description: 包含伺服器範例設定和必要的移轉步驟。
keywords: ID 服務
seo-description: 包含伺服器範例設定和必要的移轉步驟。
seo-title: Experience Cloud ID 服務移轉案例
title: Experience Cloud ID 服務移轉案例
uuid: 9e229045-6508-48c4-ae39-9537b4941853
translation-type: tm+mt
source-git-commit: 3e7b49564938527e1b6bca3a5fbaf9eb141d2e06

---


# Experience Cloud ID 服務移轉案例 {#experience-cloud-id-service-migration-scenarios}

包含伺服器範例設定和必要的移轉步驟。

## 單一 Web 屬性 {#section-6ccfea84628d46c99507cb124e7f5445}

* **客戶**: 範例 Company Inc.
* **啟用 Experience Cloud**: 否
* **Web 屬性**: example.com
* **資料收集伺服器**: metrics.example.com、smetrics.example.com
* **Analytics JavaScript 檔案**: 一個檔案用於所有網站頁面

首先，此客戶應啟用 Experience Cloud (請參閱[需求](../../reference/requirements.md))。而且，因為他們有單一 JavaScript 檔案，所以此客戶不需要寬限期。此客戶也將設定訪客移轉，然後從不需要的資料收集 CNAME 移轉走。

## 多個 JavaScript 檔案、硬式編碼影像標籤 {#section-a665f6ee202940449198e4e7a5dcac54}

* **客戶**: 其他範例 Company Inc.
* **啟用 Experience Cloud**: 是
* **Web 屬性**: anotherexample.com
* **資料收集伺服器**: anotherexampleco.112.2o7.net
* **Analytics JavaScript 檔案**: 多個 JavaScript 檔案。一個檔案用於主要網站，另一個檔案用於個別 CMS 中維護的支援區段。
* **其他資料收集方法**: 一個網站區段上的硬式編碼影像標籤

首先，此客戶應找出其 Adobe Experience Cloud 組織 ID (請參閱[需求](../../reference/requirements.md))。接著，應該設定移轉寬限期，因為他們使用多個 JavaScript 檔案。This customer will also set up visitor migration and then migrate from `*.2o7.net` to `*.sc.omtrdc.net`.

當此客戶更新至最新的 Analytics JavaScript 程式碼以準備開始使用 [!DNL Experience Cloud] ID 服務時，他們也將更新所有的硬式編碼影像標籤，以改用 JavaScript。

## 多個 Web 屬性、多個 JavaScript 檔案和 Flash 視訊播放程式 {#section-34647995ff3740b999fdee22d885e515}

* **客戶**: 有效的客戶 LLC
* **啟用 Experience Cloud**: 是
* **Web 屬性**: mymainsite.com、myothersiteA.com、myothersiteB.com
* **資料收集伺服器**: metrics.mymainsite.com、smetrics.mymainsite.com
* **Analytics JavaScript 檔案**: 多個 JavaScript 檔案。一個檔案用於每個 Web 屬性。
* **其他資料收集方法**: Flash 視訊播放程式

首先，此客戶應找出其 Adobe Experience Cloud 組織 ID (請參閱[需求](../../reference/requirements.md))。接著，應該設定移轉寬限期，因為他們使用多個 JavaScript 檔案。此客戶會在其主要網域與子網域之間追蹤訪客，因此將會繼續透過訪客 ID 服務使用其資料收集 CNAME。

當此客戶更新至最新的 Analytics JavaScript 程式碼以準備開始使用 [!DNL Experience Cloud] ID 服務時，他們也會將 Flash 視訊播放程式更新為最新版的「Flash 適用的 AppMeasurement」。
