---
description: 此選用的布林值標幟會將「Secure」屬性新增至 AMCV Cookie。
keywords: 訪客 ID 服務
title: secureCookie
exl-id: ba281b1c-1112-4ed6-b4fd-b8f87cabc575
TQID: https://experienceleague.adobe.com/UBhpXY4BvJiEDp6Adje--6ng-4W12RCWun2CpMFD3kU
product_v2: id: e1971122-7081-4556-9222-8a31bd71800c
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554id: c66ffd68-0f65-42bb-aa23-b4020f12e0bdid: f8a45b24-4be7-4f1b-909b-60d06b483a20id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
source-git-commit: 09ee359440c122702a6ce83708c98af3862c9cc9
workflow-type: tm+mt
source-wordcount: 94
ht-degree: 100%

---

# secureCookie{#securecookie}

此選用的布林值標幟會將「Secure」屬性新增至 AMCV Cookie。

`visitorAPI` 3.3.0 版提供此設定屬性。

>[!NOTE]
>
>`SecureCookie` 設定無法用於不安全的網域，且可能會導致收不到使用不安全通訊協定之造訪的 MID 值。 只有在您確定所有頁面和子網域皆隨時使用安全的通訊協定時，才應將 `secureCookie` 設定設為 `true`。

**語法：** `secureCookie: true | false`(預設)

**程式碼範例**

```js
var visitor = Visitor.getInstance("INSERT-MARKETING-CLOUD-ID-HERE",{ 
 
        //Set secure cookie property 
        secureCookie: true 
 });
```

