---
description: ECID 內部的一種配置，可用於支援 Google AMP 頁面上的 AMCV Cookie。
keywords: 訪客 ID 服務
title: 安全和 SameSite 配置
exl-id: c3bc44fc-5adc-4eae-8169-9d731d148458
TQID: https://experienceleague.adobe.com/qT9et54-InwTH7usPnjGN8mdBeMMrqK-qjxGOwqsXBA
product_v2: id: e1971122-7081-4556-9222-8a31bd71800c
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554id: c66ffd68-0f65-42bb-aa23-b4020f12e0bdid: f8a45b24-4be7-4f1b-909b-60d06b483a20id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2: id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
source-git-commit: 09ee359440c122702a6ce83708c98af3862c9cc9
workflow-type: tm+mt
source-wordcount: 151
ht-degree: 54%

---

# 安全和 SameSite 配置

此配置讓您可以更改 Cookie 設定和支援 Google AMP 頁面上的 [AMCV Cookie](../../introduction/cookies.md)。

Adobe訪客ID服務使用瀏覽器預設設定`SameSite = Lax`來設定ECID Cookie，如果頁面載入iframe （如Google AMP頁面），則無法存取。 若要存取 ECID Cookie，請使用以下配置將 SameSite 設定更新為`SameSite = None`。

>[!NOTE]
>
>套用`SameSite = None`時，必須將 Cookie 設定為`Secure`，如此才能限制僅透過 HTTPS 連線傳送資料。

**實作**：

如果您使用標籤，請將您的[!UICONTROL Experience Cloud ID Service]標籤擴充功能升級至5.1.0版，並設定`secureCookie: true`和`sameSiteCookie: none`。

如果您未使用標籤，請在初始化訪客執行個體時更新到最新的訪客5.1.0資料庫並遵循以下配置：

**程式碼範例**

```js
var visitor = Visitor.getInstance("IMSORG_ID", {

     secureCookie: true,

     sameSiteCookie: "None"

});
```

