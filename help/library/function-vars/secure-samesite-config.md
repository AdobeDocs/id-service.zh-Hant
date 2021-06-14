---
description: ECID 內部的一種配置，可用於支援 Google AMP 頁面上的 AMCV Cookie。
keywords: ID 服務
title: 安全和 SameSite 配置
exl-id: c3bc44fc-5adc-4eae-8169-9d731d148458
source-git-commit: 06e935a4ba4776baa900d3dc91e294c92b873c0f
workflow-type: ht
source-wordcount: '154'
ht-degree: 100%

---

# 安全和 SameSite 配置

此配置讓您可以更改 Cookie 設定和支援 Google AMP 頁面上的 [AMCV Cookie](../../introduction/cookies.md)。

Adobe 訪客 ID 服務使用`SameSite = Lax`的瀏覽器預設設定來設定 ECID Cookie，如果頁面以 Google AMP 頁面之類的 iframe 載入，則無法存取 ECID Cookie。若要存取 ECID Cookie，請使用以下配置將 SameSite 設定更新為`SameSite = None`。

>[!NOTE]
>
>套用`SameSite = None`時，必須將 Cookie 設定為`Secure`，如此才能限制僅透過 HTTPS 連線傳送資料。

**實作**：

如果您使用的是 Adobe Experience Platform Launch，請將您的 Experience Cloud ID 擴充功能升級到版本 5.1.0，並且配置`secureCookie: true`和`sameSiteCookie: none`。

如果您沒有使用 Experience Platform Launch，請在初始化訪客執行個體時更新到最新的訪客 5.1.0 程式庫並遵循以下配置：

**程式碼範例**

```js
var visitor = Visitor.getInstance("IMSORG_ID", {

     secureCookie: true,

     sameSiteCookie: "None"

});
```
