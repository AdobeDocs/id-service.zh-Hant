---
description: 此選用的布林值標幟會將「Secure」屬性新增至 AMCV Cookie。
keywords: ID 服務
title: secureCookie
exl-id: ba281b1c-1112-4ed6-b4fd-b8f87cabc575
source-git-commit: 06e935a4ba4776baa900d3dc91e294c92b873c0f
workflow-type: tm+mt
source-wordcount: '91'
ht-degree: 100%

---

# secureCookie{#securecookie}

此選用的布林值標幟會將「Secure」屬性新增至 AMCV Cookie。

`visitorAPI` 3.3.0 版提供此設定屬性。

>[!NOTE]
>
>`SecureCookie` 設定無法用於不安全的網域，且可能會導致收不到使用不安全通訊協定之造訪的 MID 值。只有在您確定所有頁面和子網域皆隨時使用安全的通訊協定時，才應將 `secureCookie` 設定設為 `true`。

**語法：** `secureCookie: true | false`(預設)

**程式碼範例**

```js
var visitor = Visitor.getInstance("INSERT-MARKETING-CLOUD-ID-HERE",{ 
 
        //Set secure cookie property 
        secureCookie: true 
 });
```
