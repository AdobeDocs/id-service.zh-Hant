---
description: 此選用的布林值標幟可防止訪客ID服務傳回第三方demdex.net Cookie。
keywords: 訪客 ID 服務
title: disableThirdPartyCookies
exl-id: 19d12822-0e17-4a1c-8e9c-25a22e20a4a8
TQID: https://experienceleague.adobe.com/vx9q-Q1X0fraWPUmaBlx-bBFX-gvnAox03mpENTizHw
product_v2: id: e1971122-7081-4556-9222-8a31bd71800c
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554id: c66ffd68-0f65-42bb-aa23-b4020f12e0bdid: f8a45b24-4be7-4f1b-909b-60d06b483a20id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
source-git-commit: 09ee359440c122702a6ce83708c98af3862c9cc9
workflow-type: tm+mt
source-wordcount: 144
ht-degree: 16%

---

# disableThirdPartyCookies{#disablethirdpartycookies}

此選用的布林值標幟可防止訪客ID服務傳回第三方demdex.net Cookie。

>[!NOTE]
>
>此設定原為 `idSyncDisable3rdPartySyncing`，已在 2018 年 1 月 18 日發行的 v3.0 版本中重新命名為 `disableThirdPartyCookies`。

**語法:** `disableThirdPartyCookies: true|false` (預設為 `false`。) 適用於`VisitorAPI.js` v3.0.0或更高版本。

當`disableThirdPartyCookies: true`時，訪客ID服務未傳回第三方demdex.net Cookie （請參閱[Cookie和訪客ID服務](../../introduction/cookies.md) ）。 如果網站訪客的瀏覽器中已有此Cookie，「訪客ID服務」就不會使用它來建立新的ECID或傳回現有的ID。 訪客ID服務而是會在第一方Cookie中建立新的隨機MID。 啟用後，您就可以透過訪客ID服務收集資料，並在不同的CX Enterprise解決方案中共用。

**程式碼範例**

```js
var visitor = Visitor.getInstance ("INSERT-IMS-ORG-ID-HERE",{ 
   trackingServer: "Insert tracking server here here",  //Same as s.trackingServer 
   trackingServerSecure: "Insert secure tracking server here",  //Same as s.trackingServerSecure 
 
   //For CNAME support only. Exclude these variables if you're not using CNAME 
   marketingCloudServer: "Insert tracking server here", 
   marketingCloudServerSecure: "Insert secure tracking server here", 
 
   //Function variable 
   disableThirdPartyCookies: true 
});
```

