---
description: 選用的布林值標幟，可防止訪客ID服務對其他網域進行呼叫。
keywords: 跨網域追蹤；訪客ID服務
title: 停用第三方通話
exl-id: 1d5b4e80-1b2d-4401-9057-449a6abf5db5
TQID: https://experienceleague.adobe.com/mv00QfToxSqeITADmY1LbihbtJNHf1zzQef9uKDu-dc
product_v2: id: e1971122-7081-4556-9222-8a31bd71800c
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554id: c66ffd68-0f65-42bb-aa23-b4020f12e0bdid: f8a45b24-4be7-4f1b-909b-60d06b483a20id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2: id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
source-git-commit: 09ee359440c122702a6ce83708c98af3862c9cc9
workflow-type: tm+mt
source-wordcount: 205
ht-degree: 24%

---

# 停用第三方通話{#disablethirdpartycalls}

選用的布林值標幟，可防止訪客ID服務對其他網域進行呼叫。

**語法：**` ` disableThirdPartyCalls: true|false`` (預設為 `false`false)。

當`disableThirdPartyCalls: true`時，訪客ID服務將不會呼叫其他網域。

**用途**

此變數是專為擁有以下需求的客戶所設計：

* 防止訪客ID服務從其安全、已驗證的頁面發出呼叫。
* 讓網站訪客擁有ECID。
* 讓他們的其他CX Enterprise解決方案正常運作。

**實施策略**

由於其他CX Enterprise解決方案仰賴MID，「訪客ID服務」會呼叫Adobe以傳回及設定此ID。 如果您需要停止訪客ID服務從已驗證的網站區域進行呼叫，請讓它先從不需要驗證的頁面進行必要的呼叫。 您的網站訪客擁有MID之後，您就可以在已驗證網站區段的訪客ID服務程式碼中設定`disableThirdPartyCalls= true`。 這裡假設您的大多數客戶 (如果不是所有客戶的話) 都會先導覽至驗證頁面，然後才會存取您網站的安全部分。

**程式碼範例**

```js
var visitor = Visitor.getInstance ("INSERT-IMS-ORG-ID-HERE",{ 
   trackingServer: "Insert tracking server here here",  //Same as s.trackingServer 
   trackingServerSecure: "Insert secure tracking server here",  //Same as s.trackingServerSecure 
 
   //For CNAME support only. Exclude these variables if you're not using CNAME 
   marketingCloudServer: "Insert tracking server here", 
   marketingCloudServerSecure: "Insert secure tracking server here", 
 
   //Function variable 
   disableThirdPartyCalls: true 
}); 
```

