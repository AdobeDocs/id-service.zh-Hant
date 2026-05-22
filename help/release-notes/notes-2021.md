---
description: Experience Cloud 身分識別服務的功能發佈、更新或變更。
keywords: ID 服務
title: 2021 年發行說明
exl-id: 56bffb6f-a4fc-40df-8bb2-17e43772fe60
TQID: https://experienceleague.adobe.com/AB8VuYn9X41P9REJ8C215GzBRtH66lb35i-q1PNbZfU
product_v2: id: e1971122-7081-4556-9222-8a31bd71800c
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554id: c66ffd68-0f65-42bb-aa23-b4020f12e0bdid: f8a45b24-4be7-4f1b-909b-60d06b483a20id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2: id: f4e6943a-c91a-4134-a2c7-f4f20cfff2f0
source-git-commit: 5c41e39a833b527a329f62e5f0929445f47139de
workflow-type: tm+mt
source-wordcount: 110
ht-degree: 100%

---

# Experience Cloud 身分識別服務發行說明 - 2021

Experience Cloud 身分識別服務的功能發佈、更新或變更。

## Visitor 5.3.0

Visitor 5.3.0 版包含下列更新：

* 更新演算法以產生本機 ECID。
* 最新的選擇加入，包含 `Secure` 和 `SameSite` 標幟用於隱私 Cookie。
* 修補程式修復頁面載入至子 iFrame 時的 Firefox 瀏覽器問題。

## Visitor 5.2.0

Visitor 5.2.0 版包含下列更新：

* 此版本引進 `onReceiveEcid` 事件，從身分識別服務接收到 ECID 時會呼叫它。 例如:

```js
visitorInstance.onReceiveEcid(callback(ecid){
 console.log(ecid)
})
```

