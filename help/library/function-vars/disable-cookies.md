---
description: 此選用的布林值標幟可防止 Experience Cloud Identity 服務傳回第三方 demdex.net Cookie。
keywords: ID Service
seo-description: 此選用的布林值標幟可防止 Experience Cloud Identity 服務傳回第三方 demdex.net Cookie。
seo-title: disableThirdPartyCookies
title: disableThirdPartyCookies
uuid: 7ed5aa16-44ca-4702-878a-1a208ca95270
translation-type: tm+mt
source-git-commit: 584b6240c3e0286111689499ca5df5d98aa9fab2
workflow-type: tm+mt
source-wordcount: '155'
ht-degree: 60%

---


# disableThirdPartyCookies{#disablethirdpartycookies}

此選用的布林值標幟可防止 Experience Cloud Identity 服務傳回第三方 demdex.net Cookie。

>[!NOTE]
>
>此設定原為 `idSyncDisable3rdPartySyncing`，已在 2018 年 1 月 18 日發行的 v3.0 版本中重新命名為 `disableThirdPartyCookies`。

**語法:** `disableThirdPartyCookies: true|false` (預設為 `false`。)適用於 `VisitorAPI.js` v3.0.0 或更高版本。

當 `disableThirdPartyCookies: true` 時，ID 服務不會傳回第三方 demdex.net Cookie (請參閱 [Cookie 與 Experience Cloud Identity 服務](../../introduction/cookies.md))。如果網站訪客的瀏覽器中已有此Cookie,ID服務將不會使用它建立新的Experience Cloud ID(MID)或傳回現有ID。 ID服務會在第一方Cookie中建立新的隨機MID。 啟用後，您就可以使用ID服務收集資料，並在不同的Experience Cloud解決方案間共用資料。

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

