---
description: 選用的布林值標幟，可防止 ID 服務對其他網域進行呼叫。
keywords: 跨網域追蹤;ID 服務
title: 停用第三方通話
exl-id: 1d5b4e80-1b2d-4401-9057-449a6abf5db5
source-git-commit: 06e935a4ba4776baa900d3dc91e294c92b873c0f
workflow-type: ht
source-wordcount: '200'
ht-degree: 100%

---

# 停用第三方通話{#disablethirdpartycalls}

選用的布林值標幟，可防止 ID 服務對其他網域進行呼叫。

**語法：**` ` disableThirdPartyCalls: true|false`` (預設為 `false`false)。

若 `disableThirdPartyCalls: true`，ID 服務將不會呼叫其他網域。

**用途**

此變數是專為擁有以下需求的客戶所設計：

* 讓 ID 服務無法從其安全、受驗證的頁面發出呼叫。
* 讓網站訪客擁有 Experience Cloud ID (MID)。
* 讓他們的其他 Experience Cloud 解決方案正常運作。

**實作策略**

由於其他 Experience Cloud 解決方案仰賴 MID，所以 ID 服務會呼叫 Adobe 以傳回及設定此 ID。如果您想停止 ID 服務從已驗證的網站區域進行呼叫，請讓 ID 服務先從不需要驗證的頁面進行必要的呼叫。等網站訪客擁有 MID 後，您就能在已驗證網站區域的 ID 服務程式碼中設定 `disableThirdPartyCalls= true`。這裡假設您的大多數客戶 (如果不是所有客戶的話) 都會先導覽至驗證頁面，然後才會存取您網站的安全部分。

**程式碼範例**

```js
var visitor = Visitor.getInstance ("Insert Experience Cloud organization ID here",{ 
   trackingServer: "Insert tracking server here here",  //Same as s.trackingServer 
   trackingServerSecure: "Insert secure tracking server here",  //Same as s.trackingServerSecure 
 
   //For CNAME support only. Exclude these variables if you're not using CNAME 
   marketingCloudServer: "Insert tracking server here", 
   marketingCloudServerSecure: "Insert secure tracking server here", 
 
   //Function variable 
   disableThirdPartyCalls: true 
}); 
```
