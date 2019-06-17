---
description: 此選用的布林值標幟會將「Secure」屬性新增至 AMCV Cookie。
keywords: ID 服務
seo-description: 此選用的布林值標幟會將「Secure」屬性新增至 AMCV Cookie。
seo-title: secureCookie
title: secureCookie
uuid: 995d19f6-9c9d-4493-9c9c-545b0b5696b0
translation-type: tm+mt
source-git-commit: bb687c1cd14aae7faef2565dcf9d041a1c06e3bd

---


# secureCookie{#securecookie}

此選用的布林值標幟會將「Secure」屬性新增至 AMCV Cookie。

此組態屬性適用於 `visitorAPI`3.3.0版。

>[!NOTE]
>
>`SecureCookie` 此設定不適用於不安全的網域，可能導致您無法接收使用非安全通訊協定之瀏覽的MID值。只有在您確定所有頁面和子網域皆隨時使用安全的通訊協定時，才應將 `secureCookie` 設定設為 `true`。

**語法：**`secureCookie: true | false` (預設)

**程式碼範例**

```js
var visitor = Visitor.getInstance("INSERT-MARKETING-CLOUD-ID-HERE",{ 
 
        //Set secure cookie property 
        secureCookie: true 
 });
```

