---
description: Experience Cloud Identity 服務的功能發佈、更新或變更。
keywords: ID 服務
title: 2021年發行說明
source-git-commit: dce2c0036f697507381d0763c2f6a9538155681c
workflow-type: tm+mt
source-wordcount: '103'
ht-degree: 25%

---

# Experience CloudIdentity Service發行說明 — 2021

Experience Cloud Identity Service 的功能發佈、更新或變更。

## 訪客5.3.0

Visitor 5.3.0版包含下列更新：

* 更新演算法以產生本機ECID。
* 使用 `Secure` 和 `SameSite` 隱私權cookie的旗標。
* 在子iFrame中載入頁面時，Firefox瀏覽器問題的修補程式修正。

## 訪客5.2.0

Visitor 5.2.0版包含下列更新：

* 此版本會導入事件 `onRecieveEcid`，從Identity Service收到ECID時，系統會呼叫此ID。 例如：

```js
visitorInstance.onRecieveEcid(callback(ecid){
 console.log(ecid)
})
```
