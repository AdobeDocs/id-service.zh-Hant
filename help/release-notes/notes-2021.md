---
description: Experience Cloud Identity Service 的功能發佈、更新或變更。
keywords: ID 服務
title: 2021 年發行說明
exl-id: f0bbb100-49a9-4bba-8cee-5f40bec87984
source-git-commit: fcd3e8b65bb84e94eabac7ffec6a34f4cf75ec3d
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

* 此版本引進 `onRecieveEcid` 事件，從 Identity Service 接收到 ECID 時會呼叫它。例如：

```js
visitorInstance.onRecieveEcid(callback(ecid){
 console.log(ecid)
})
```
