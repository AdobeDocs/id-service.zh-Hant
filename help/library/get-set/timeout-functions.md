---
description: 呼叫這些 ID 服務函數可判斷 Experience Cloud Identity 服務、Analytics 或 Audience Manager ID 要求的逾時狀態。適用於 VisitorAPI.js 1.7.0 版或更新版本。
keywords: ID 服務
seo-description: 呼叫這些 ID 服務函數可判斷 Experience Cloud Identity 服務、Analytics 或 Audience Manager ID 要求的逾時狀態。適用於 VisitorAPI.js 1.7.0 版或更新版本。
seo-title: callTimeOut 方法
title: callTimeOut 方法
uuid: e5047498-11db-4945-b356-c92b7d447573
translation-type: ht
source-git-commit: e6d65f1bfed187d7440512e8f3c2de0550506c95

---


# callTimeOut 方法{#calltimeout-methods}

呼叫這些 ID 服務函數可判斷 Experience Cloud Identity 服務、Analytics 或 Audience Manager ID 要求的逾時狀態。適用於 VisitorAPI.js 1.7.0 版或更新版本。

## 逾時函數{#section-e08228ef5f9b45c9a84139bbb763164a}

<table id="table_B3ACE584B3224D838070D32A8462EF28"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> 解決方案或服務 </th> 
   <th colname="col2" class="entry"> 函數語法 </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p>Experience Cloud Identity 服務 </p> </td> 
   <td colname="col2"> <p> <span class="codeph">var <span class="varname"> variableName</span> = visitor.MCIDCallTimedOut()</span> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="keyword"> Analytics</span> </p> </td> 
   <td colname="col2"> <p> <span class="codeph">var <span class="varname"> variableName</span> = visitor.AnalyticsIDCallTimedOut()</span> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="keyword"> Audience Manager</span> </p> </td> 
   <td colname="col2"> <p> <span class="codeph">var <span class="varname"> variableName</span> = visitor.AAMIDCallTimedOut()</span> </p> </td> 
  </tr> 
 </tbody> 
</table>

## 函數回應 {#section-ff73aaca58b74e10a0953c49a3387160}

<table id="table_5D08A5DD6FD04F94818B0E8B790D3136"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> 回應 </th> 
   <th colname="col2" class="entry"> 說明 </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> TRUE</span> </p> </td> 
   <td colname="col2"> <p>ID 服務傳送要求，但要求逾時。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> FALSE</span> </p> </td> 
   <td colname="col2"> <p>ID 服務傳送要求，並從伺服器收到成功回應。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> NULL</span> </p> </td> 
   <td colname="col2"> <p>ID 服務未傳送要求。 </p> </td> 
  </tr> 
 </tbody> 
</table>

