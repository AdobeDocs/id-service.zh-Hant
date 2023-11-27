---
description: Experience Cloud Identity Service 的功能發佈、更新或變更。
keywords: ID 服務
title: 2021 年發行說明
exl-id: 56bffb6f-a4fc-40df-8bb2-17e43772fe60
source-git-commit: 52956b38c59f60507aaf236b152ce41fc1229d14
workflow-type: ht
source-wordcount: '103'
ht-degree: 100%

---

# Experience Cloud Identity Service 發行說明 - 2021

Experience Cloud Identity Service 的功能發佈、更新或變更。

## Visitor 5.3.0

Visitor 5.3.0 版包含下列更新：

* 更新演算法以產生本機 ECID。
* 最新的選擇加入，包含 `Secure` 和 `SameSite` 標幟用於隱私 Cookie。
* 修補程式修復頁面載入至子 iFrame 時的 Firefox 瀏覽器問題。

## Visitor 5.2.0

Visitor 5.2.0 版包含下列更新：

* 此版本引進 `onReceiveEcid` 事件，從 Identity Service 接收到 ECID 時會呼叫它。例如：

```js
visitorInstance.onReceiveEcid(callback(ecid){
 console.log(ecid)
})
```
