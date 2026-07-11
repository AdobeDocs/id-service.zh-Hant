---
description: 訪客ID服務的標準與非標準實作方法。
keywords: 訪客 ID 服務
title: 實作方法
exl-id: 0fe40a3c-bdcd-4290-bcd7-25344ff108d6
TQID: https://experienceleague.adobe.com/VcMKVPqOHJHqwX4CTYHeeQnqrEzwLLJ9xn2-e1vDr-k
product_v2: id: e1971122-7081-4556-9222-8a31bd71800c
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554id: c66ffd68-0f65-42bb-aa23-b4020f12e0bdid: f8a45b24-4be7-4f1b-909b-60d06b483a20id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2: id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
source-git-commit: 09ee359440c122702a6ce83708c98af3862c9cc9
workflow-type: tm+mt
source-wordcount: 151
ht-degree: 33%

---

# 實作方法

您可以選擇使用標籤的標準訪客ID服務實作方法，或非標準實作方法。

>[!IMPORTANT]
>
>開始進行這些程式之前，請務必閱讀並瞭解[訪客ID服務需求](../reference/requirements.md)。

## 標準實作 {#section-ea1e5270f2184f85a2e85214a6ac60cb}

Adobe強烈建議使用[標籤](https://experienceleague.adobe.com/docs/experience-platform/tags/home.html?lang=zh-Hant)來實作訪客ID服務。 此方法可確保整合其他CX Enterprise解決方案、簡化實作工作流程，並自動確保程式碼的位置和順序正確無誤。

## 非標準實作 {#section-2c4f2db1f9704315a7cccab6d2e07113}

本指南中的程式和程式碼範例可協助您以手動或非標準方式來設定訪客ID服務。 請注意，這些實作通常在技術上較複雜並具有挑戰性。 您可能需要稀有的工程師人力，或必須用掉 Adobe 顧問合約支援時間。

