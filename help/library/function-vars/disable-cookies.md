---
description: 此選用的布林值標幟可防止 Experience Cloud Identity 服務傳回第三方 demdex.net Cookie。
keywords: ID 服務
seo-description: 此選用的布林值標幟可防止 Experience Cloud Identity 服務傳回第三方 demdex.net Cookie。
seo-title: disableThirdPartyCookies
title: disableThirdPartyCookies
uuid: 7ed5aa16-44ca-4702-878a-1a208ca95270
translation-type: ht
source-git-commit: 584b6240c3e0286111689499ca5df5d98aa9fab2

---


# disableThirdPartyCookies{#disablethirdpartycookies}

此選用的布林值標幟可防止 Experience Cloud Identity 服務傳回第三方 demdex.net Cookie。

>[!NOTE]
>
>此設定原為 `idSyncDisable3rdPartySyncing`，已在 2018 年 1 月 18 日發行的 v3.0 版本中重新命名為 `disableThirdPartyCookies`。

**語法:** `disableThirdPartyCookies: true|false` (預設為 `false`。)適用於 `VisitorAPI.js` v3.0.0 或更高版本。

當 `disableThirdPartyCookies: true` 時，ID 服務不會傳回第三方 demdex.net Cookie (請參閱 [Cookie 與 Experience Cloud Identity 服務](../../introduction/cookies.md))。如果網站訪客在瀏覽器中已擁有此 Cookie，ID 服務不會使用該 Cookie 來建立新的 Experience Cloud ID (MID) 或傳回現有 ID。相反地，ID 服務會在第一方 Cookie 中建立新的隨機 ID。啟用後，您可以利用 ID 服務收集資料，並在不同的 Experience Cloud 解決方案之間共用資料。

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

