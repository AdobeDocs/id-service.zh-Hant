---
description: 呼叫此 ID 服務函數，以判斷 ID 服務是否產生了用戶端、Experience Cloud 訪客 ID (MID)。適用於 VisitorAPI.js 1.7.0 版或更新版本。
keywords: ID 服務
seo-description: 呼叫此 ID 服務函數，以判斷 ID 服務是否產生了用戶端、Experience Cloud 訪客 ID (MID)。適用於 VisitorAPI.js 1.7.0 版或更新版本。
seo-title: isClientSideMarketingCloudVisitorID
title: isClientSideMarketingCloudVisitorID
uuid: 1c39ac60-1d2b-4ed4-a2ea-30d680e61e10
exl-id: ed2672e7-da1a-4c02-9f4e-c14419ec9ec7
translation-type: ht
source-git-commit: 4453ebf701ea2dc06e6093dd77be6eb0f3b2936e
workflow-type: ht
source-wordcount: '148'
ht-degree: 100%

---

# isClientSideMarketingCloudVisitorID{#isclientsidemarketingcloudvisitorid}

呼叫此 ID 服務函數，以判斷 ID 服務是否產生了用戶端、Experience Cloud 訪客 ID (MID)。適用於 VisitorAPI.js 1.7.0 版或更新版本。

**語法**

`var *`variableName`* = visitor.isClientSideMarketingCloudVisitorID()`

下表列出及說明此函數傳回的回應。

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
