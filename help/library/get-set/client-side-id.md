---
description: 呼叫此ID服務函式，以判斷ID服務是否產生用戶端Experience Cloud訪客ID(MID)。 適用於 VisitorAPI.js 1.7.0 版或更新版本。
keywords: ID Service
seo-description: 呼叫此ID服務函式，以判斷ID服務是否產生用戶端Experience Cloud訪客ID(MID)。 適用於 VisitorAPI.js 1.7.0 版或更新版本。
seo-title: isClientSideMarketingCloudVisitorID
title: isClientSideMarketingCloudVisitorID
uuid: 1c39ac60-1d2b-4ed4-a2ea-30d680e61e10
translation-type: tm+mt
source-git-commit: bc5c81455023e22e64877bb861dfe141e158599c
workflow-type: tm+mt
source-wordcount: '146'
ht-degree: 52%

---


# isClientSideMarketingCloudVisitorID{#isclientsidemarketingcloudvisitorid}

呼叫此ID服務函式，以判斷ID服務是否產生用戶端Experience Cloud訪客ID(MID)。 適用於 VisitorAPI.js 1.7.0 版或更新版本。

**語法**

`var *`variableName`* = visitor.isClientSideMarketingCloudVisitorID()`

下表列出並說明此函式傳回的回應。

<table id="table_5D08A5DD6FD04F94818B0E8B790D3136"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> 回應 </th> 
   <th colname="col2" class="entry"> 說明 </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> true</span> </p> </td> 
   <td colname="col2"> <p>ID 服務收不到來自 <span class="keyword">Experience Cloud</span> 伺服器的 MID。它已在本機的瀏覽器中建立 MID (用戶端)。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> false</span> </p> </td> 
   <td colname="col2"> <p>ID 服務收到來自 <span class="keyword">Experience Cloud</span> 伺服器的 MID。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> null</span> </p> </td> 
   <td colname="col2"> <p>ID 服務未對 <span class="keyword">Experience Cloud</span> 伺服器進行呼叫。 </p> </td> 
  </tr> 
 </tbody> 
</table>

