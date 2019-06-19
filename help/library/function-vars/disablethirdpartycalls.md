---
description: 選用的布林值標幟，可防止 ID 服務對其他網域進行呼叫。
keywords: 跨網域追蹤；ID服務
seo-description: 選用的布林值標幟，可防止 ID 服務對其他網域進行呼叫。
seo-title: 停用第三方通話
title: 停用第三方通話
uuid: e92ce1f5-67a4-476c-9d04-41d4e96b1592
translation-type: tm+mt
source-git-commit: bc5c81455023e22e64877bb861dfe141e158599c

---


# 停用第三方通話{#disablethirdpartycalls}

選用的布林值標幟，可防止 ID 服務對其他網域進行呼叫。

**語法：**` `disableThirdPartyCalls：true| false」(預設為 `false`。)

若 `disableThirdPartyCalls: true`，ID 服務將不會呼叫其他網域。

**用途**

此變數設計給有下列需求的客戶:

* 想防止 ID 服務從其安全的已驗證頁面進行呼叫。
* 要求網站訪客具有 Experience Cloud ID (MID)。
* 其他 Experience Cloud 解決方案運作正常。

**實施策略**

由於其他 Experience Cloud 解決方案需倚賴 MID，ID 服務會呼叫 Adobe 以傳回並設定這個 ID。如果您想停止 ID 服務從已驗證的網站區域進行呼叫，請讓 ID 服務先從不需要驗證的頁面進行必要的呼叫。等網站訪客擁有 MID 後，您就能在已驗證網站區域的 ID 服務程式碼中設定 `disableThirdPartyCalls= true`。此處運用的假設是，大部分客戶必須先瀏覽至驗證頁面，才能取得網站安全部分的存取權限。

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

