---
description: 此選用的布林值標幟可防止 Experience Cloud Identity 服務傳回第三方 demdex.net Cookie。
keywords: ID 服務
title: disableThirdPartyCookies
exl-id: 19d12822-0e17-4a1c-8e9c-25a22e20a4a8
source-git-commit: 06e935a4ba4776baa900d3dc91e294c92b873c0f
workflow-type: tm+mt
source-wordcount: '139'
ht-degree: 100%

---

# disableThirdPartyCookies{#disablethirdpartycookies}

此選用的布林值標幟可防止 Experience Cloud Identity 服務傳回第三方 demdex.net Cookie。

>[!NOTE]
>
>此設定原為 `idSyncDisable3rdPartySyncing`，已在 2018 年 1 月 18 日發行的 v3.0 版本中重新命名為 `disableThirdPartyCookies`。

**語法：**`disableThirdPartyCookies: true|false` (預設為 `false`。)適用於 `VisitorAPI.js` v3.0.0 或更高版本。

當 `disableThirdPartyCookies: true` 時，ID 服務不會傳回第三方 demdex.net Cookie (請參閱 [Cookie 與 Experience Cloud Identity 服務](../../introduction/cookies.md))。如果網站訪客在瀏覽器中已擁有此 Cookie，ID 服務將不會使用該 Cookie 來建立新的 Experience Cloud ID (MID) 或傳回現有 ID。ID 服務而是會在第一方 Cookie 中建立新的隨機 MID。在啟用後，您可以使用 ID 服務收集資料，並在不同的 Experience Cloud 解決方案中分享。

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
