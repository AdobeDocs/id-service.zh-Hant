---
description: 呼叫此訪客ID服務函式，判斷訪客ID服務是否產生了使用者端ECID (MID)。 適用於 VisitorAPI.js 1.7.0 版或更新版本。
keywords: 訪客 ID 服務
title: isClientSideMarketingCloudVisitorID
exl-id: ed2672e7-da1a-4c02-9f4e-c14419ec9ec7
TQID: https://experienceleague.adobe.com/kQK7Lw-j33luPqTSzQKGuf8fMPuOEDoQBzesZa-bvVo
product_v2:
  - id: e1971122-7081-4556-9222-8a31bd71800c
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: f8a45b24-4be7-4f1b-909b-60d06b483a20
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
source-git-commit: 09ee359440c122702a6ce83708c98af3862c9cc9
workflow-type: tm+mt
source-wordcount: 128
ht-degree: 32%

---

# isClientSideMarketingCloudVisitorID{#isclientsidemarketingcloudvisitorid}

呼叫此訪客ID服務函式，判斷訪客ID服務是否產生了使用者端ECID (MID)。 可用於`VisitorAPI.js` 1.7.0版或更新版本。

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
   <td colname="col2"> <p>訪客ID服務無法或沒有從CX Enterprise伺服器收到MID。 它已在本機的瀏覽器中建立 MID (用戶端)。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> false</span> </p> </td> 
   <td colname="col2"> <p>訪客ID服務收到來自CX Enterprise伺服器的MID。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> null</span> </p> </td> 
   <td colname="col2"> <p>訪客ID服務沒有對CX Enterprise伺服器進行呼叫。 </p> </td> 
  </tr> 
 </tbody> 
</table>

