---
description: Experience Cloud Identity Service 的功能發佈、更新或變更。
keywords: ID 服務
title: 2020 年版本注意事項
exl-id: c9d7876e-debc-4c8e-8ebc-91646610c876
source-git-commit: cb89ac70e37f35d5e4e2b971f2df9645304522f8
workflow-type: ht
source-wordcount: '132'
ht-degree: 100%

---

# Experience Cloud 版本注意事項 - 2020 {#release-notes}

提供 Experience Cloud Identity Service (ECID) 的功能發佈、更新或變更資訊。

## 4.6 版

* 預設為 `loadSSL` 標幟開啟。所有對 Identity 服務的呼叫均預設為透過 `https` 發出。如果客戶想從 `non-ssl` 頁面透過 http 呼叫 Identity 服務，可將其設為 false。
* 更新偵測 `Internet-Explorer (IE)` 版本的函數，以修正 `ESLint` 回報的問題。
修正 ECID 收到選擇加入 `Internet-Explorer (IE) 11` 及稍後更新時 `pre-approval` 的效能問題。

## 4.5 版

* 從 4.5 版開始，ECID 不允許用戶傳送空 ID 至 `setCustomerIDs` 方法。
* 修正選擇加入功能設為 `doesOptInApply=false` 和 `isIabContext=true` 時發生的問題。

如需查看所有產品每個月的版本注意事項，請參閱 [Experience Cloud 版本注意事項](https://experienceleague.adobe.com/docs/release-notes/experience-cloud/current.html?lang=zh-Hant)。
