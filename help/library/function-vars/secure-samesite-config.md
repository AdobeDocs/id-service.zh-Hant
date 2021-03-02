---
description: ECID中可用來支援Google AMP頁面上AMCV Cookie的組態。
keywords: ID 服務
seo-description: ECID中可用來支援Google AMP頁面上AMCV Cookie的組態。
seo-title: 安全與相同網站組態
title: 安全與相同網站組態
translation-type: tm+mt
source-git-commit: 702d20f3989f7749fb173496765d94c3a5af46dc
workflow-type: tm+mt
source-wordcount: '174'
ht-degree: 2%

---


# 安全與相同網站組態

此設定可讓您變更Cookie的設定，並支援Google AMP頁面上的[AMCV Cookie](../../introduction/cookies.md)。

Adobe訪客ID服務會以瀏覽器預設設定`SameSite = Lax`來設定ECID Cookie，如果頁面載入如Google AMP頁面的iframe，將無法存取此設定。 若要存取ECID Cookie，請使用下列組態將SameSite設定更新為`SameSite = None`。

>[!NOTE]
>
>套用`SameSite = None`時，Cookie必須設為`Secure`，如此才能透過HTTPS連線傳送資料。

**實作**:

如果您使用Adobe Experience Platform Launch，請將Experience CloudID擴充功能升級至5.1.0版，並設定`secureCookie: true`和`sameSiteCookie: none`。

如果您未使用Experience Platform Launch，請更新至最新的訪客5.1.0程式庫，並遵循下列設定，同時初始化訪客例項：

**程式碼範例**

```js
var visitor = Visitor.getInstance("IMSORG_ID", {

     secureCookie: true,

     sameSiteCookie: "None"

});
```
