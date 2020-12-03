---
description: 包含伺服器範例設定和必要的移轉步驟。
keywords: ID Service
seo-description: 包含伺服器範例設定和必要的移轉步驟。
seo-title: Experience Cloud Identity 服務移轉案例
title: Experience Cloud Identity 服務移轉案例
uuid: 9e229045-6508-48c4-ae39-9537b4941853
translation-type: tm+mt
source-git-commit: e6d65f1bfed187d7440512e8f3c2de0550506c95
workflow-type: tm+mt
source-wordcount: '393'
ht-degree: 46%

---


# Experience Cloud Identity 服務移轉案例 {#experience-cloud-id-service-migration-scenarios}

包含伺服器範例設定和必要的移轉步驟。

## 單一 Web 屬性 {#section-6ccfea84628d46c99507cb124e7f5445}

* **客戶**: 範例 Company Inc.
* **Experience Cloud已啟用**:否
* **Web屬性**:example.com
* **資料收集伺服器**:metrics.example.com, smetrics.example.com
* **Analytics JavaScript檔案**:所有網站頁面的單一檔案

首先，此客戶應啟用Experience Cloud(請參閱 [需求](../../reference/requirements.md))。 此外，由於客戶有單一JavaScript檔案，因此此客戶不需要寬限期。 此客戶也會設定訪客移轉，然後移轉離開其資料收集CNAME（不需要）。

## 多個 JavaScript 檔案、硬式編碼影像標籤 {#section-a665f6ee202940449198e4e7a5dcac54}

* **客戶**: 其他範例 Company Inc.
* **Experience Cloud已啟用**:是
* **Web屬性**:anotherexample.com
* **資料收集伺服器**:anotherexampleco.112.2o7.net
* **Analytics JavaScript檔案**:多個JavaScript檔案。 一個檔案用於其主網站，另一個檔案用於其支援區段，並保留在個別的CMS中。
* **其他資料收集方法**:一個網站區段上的硬式編碼影像標籤

首先，此客戶應找到其Adobe Experience Cloud組織ID(請參閱 [要求](../../reference/requirements.md))。 接著，應該設定移轉寬限期，因為他們使用多個 JavaScript 檔案。此客戶也將設定訪客移轉，然後從 `*.2o7.net` 移轉至 `*.sc.omtrdc.net`。

當此客戶更新至最新的 Analytics JavaScript 程式碼以準備開始使用 [!DNL Experience Cloud] ID 服務時，他們也將更新所有的硬式編碼影像標籤，以改用 JavaScript。

## 多個 Web 屬性、多個 JavaScript 檔案和 Flash 視訊播放程式 {#section-34647995ff3740b999fdee22d885e515}

* **客戶**: 有效的客戶 LLC
* **Experience Cloud已啟用**:是
* **Web屬性**:mymainsite.com、myothersiteA.com、myothersiteB.com
* **資料收集伺服器**:metrics.mymainsite.com, smetrics.mymainsite.com
* **Analytics JavaScript檔案**:多個JavaScript檔案。 每個Web屬性都有一個檔案。
* **其他資料收集方法**:Flash視訊播放器

首先，此客戶應找到其Adobe Experience Cloud組織ID(請參閱 [要求](../../reference/requirements.md))。 接著，應該設定移轉寬限期，因為他們使用多個 JavaScript 檔案。此客戶會在其主要網域和子網域之間追蹤訪客，因此他們將繼續與訪客ID服務一起使用其資料收集CNAME。

當此客戶更新至最新的 Analytics JavaScript 程式碼以準備開始使用 [!DNL Experience Cloud] ID 服務時，他們也會將 Flash 視訊播放程式更新為最新版的「Flash 適用的 AppMeasurement」。
