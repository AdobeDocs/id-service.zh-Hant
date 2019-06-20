---
description: 選用的布林值標幟，可防止Experience Cloud ID服務傳回第三方、demdex. net Cookie。
keywords: ID 服務
seo-description: 選用的布林值標幟，可防止Experience Cloud ID服務傳回第三方、demdex. net Cookie。
seo-title: disableThirdPartyCookies
title: disableThirdPartyCookies
uuid: 7ed5aa16-44ca-4702-878a-1a208ca95270
translation-type: tm+mt
source-git-commit: 3e7b49564938527e1b6bca3a5fbaf9eb141d2e06

---


# disableThirdPartyCookies{#disablethirdpartycookies}

選用的布林值標幟，可防止Experience Cloud ID服務傳回第三方、demdex. net Cookie。

>[!NOTE]
>
>This configuration was `idSyncDisable3rdPartySyncing` and renamed to `disableThirdPartyCookies` in the January 18, 2018 release of v3.0.

**語法：**`disableThirdPartyCookies: true|false` (預設 `false`為。)`VisitorAPI.js` 針對v1.5.3或更新版本。

When `disableThirdPartyCookies: true`, the ID service does not return the third-party, demdex.net cookie (see [Cookies and the Experience Cloud ID Service](../../introduction/cookies.md) ). 如果網站訪客在瀏覽器中已擁有此 Cookie，ID 服務不會使用該 Cookie 來建立新的 Experience Cloud ID (MID) 或傳回現有 ID。相反地，ID 服務會在第一方 Cookie 中建立新的隨機 ID。啟用後，您可以利用 ID 服務收集資料，並在不同的 Experience Cloud 解決方案之間共用資料。

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

