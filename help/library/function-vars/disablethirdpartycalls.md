---
description: 選用的布林值標幟，可防止 ID 服務對其他網域進行呼叫。
keywords: cross domain tracking;ID Service
seo-description: 選用的布林值標幟，可防止 ID 服務對其他網域進行呼叫。
seo-title: 停用第三方通話
title: 停用第三方通話
uuid: e92ce1f5-67a4-476c-9d04-41d4e96b1592
translation-type: tm+mt
source-git-commit: bc5c81455023e22e64877bb861dfe141e158599c
workflow-type: tm+mt
source-wordcount: '211'
ht-degree: 58%

---


# 停用第三方通話{#disablethirdpartycalls}

選用的布林值標幟，可防止 ID 服務對其他網域進行呼叫。

**語法:** ` ` disableThirdPartyCalls: true|false`` (預設為 `false`false)。

若 `disableThirdPartyCalls: true`，ID 服務將不會呼叫其他網域。

**用途**

此變數是專為需要：

* 防止ID服務從其安全、已驗證的頁面進行呼叫。
* 擁有Experience Cloud ID(MID)的網站訪客。
* 其他Experience Cloud解決方案可正常運作。

**實作策略**

由於其他Experience Cloud解決方案依賴MID,ID服務會呼叫Adobe以傳回並設定此ID。 如果您想停止 ID 服務從已驗證的網站區域進行呼叫，請讓 ID 服務先從不需要驗證的頁面進行必要的呼叫。等網站訪客擁有 MID 後，您就能在已驗證網站區域的 ID 服務程式碼中設定 `disableThirdPartyCalls= true`。這裡的假設是，大部分（如果不是全部）客戶在存取您網站的安全部分之前，都會導覽至驗證頁面。

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

