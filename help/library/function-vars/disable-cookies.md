---
description: 此選用的布林值標幟可防止 Experience Cloud 身分識別服務傳回第三方 demdex.net Cookie。
keywords: ID 服務
title: disableThirdPartyCookies
exl-id: 19d12822-0e17-4a1c-8e9c-25a22e20a4a8
TQID: https://experienceleague.adobe.com/vx9q-Q1X0fraWPUmaBlx-bBFX-gvnAox03mpENTizHw
product_v2: id: e1971122-7081-4556-9222-8a31bd71800c
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554id: c66ffd68-0f65-42bb-aa23-b4020f12e0bdid: f8a45b24-4be7-4f1b-909b-60d06b483a20id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
source-git-commit: 5c41e39a833b527a329f62e5f0929445f47139de
workflow-type: tm+mt
source-wordcount: 145
ht-degree: 97%

---

# disableThirdPartyCookies{#disablethirdpartycookies}

此選用的布林值標幟可防止 Experience Cloud 身分識別服務傳回第三方 demdex.net Cookie。

>[!NOTE]
>
>此設定原為 `idSyncDisable3rdPartySyncing`，已在 2018 年 1 月 18 日發行的 v3.0 版本中重新命名為 `disableThirdPartyCookies`。

**語法:** `disableThirdPartyCookies: true|false` (預設為 `false`。) 適用於`VisitorAPI.js` v3.0.0或更高版本。

當 `disableThirdPartyCookies: true` 時，ID 服務不會傳回第三方 demdex.net Cookie (請參閱 [Cookie 與 Experience Cloud 身分識別服務](../../introduction/cookies.md))。 如果網站訪客在瀏覽器中已擁有此 Cookie，ID 服務將不會使用該 Cookie 來建立新的 Experience Cloud ID (MID) 或傳回現有 ID。 ID 服務而是會在第一方 Cookie 中建立新的隨機 MID。 在啟用後，您可以使用 ID 服務收集資料，並在不同的 Experience Cloud 解決方案中分享。

**程式碼範例**

```js
var visitor = Visitor.getInstance ("Insert Experience Cloud organization ID here",{ 
   trackingServer: "Insert tracking server here here",  //Same as s.trackingServer 
   trackingServerSecure: "Insert secure tracking server here",  //Same as s.trackingServerSecure 
 
   //For CNAME support only. Exclude these variables if you're not using CNAME 
   marketingCloudServer: "Insert tracking server here", 
   marketingCloudServerSecure: "Insert secure tracking server here", 
 
   //Function variable 
   disableThirdPartyCookies: true 
});
```

