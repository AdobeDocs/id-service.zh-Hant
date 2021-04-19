---
description: 管理選擇加入服務的使用案例與解決方案範例。
seo-description: 管理選擇加入服務的使用案例與解決方案範例。
seo-title: 選擇加入使用案例
title: 選擇加入使用案例
uuid: d75a44d5-b713-43d1-b5b6-95d1d0d213a7
exl-id: 4c57685f-40b7-4af4-8527-3c2795586f0f
translation-type: ht
source-git-commit: 4453ebf701ea2dc06e6093dd77be6eb0f3b2936e
workflow-type: ht
source-wordcount: '437'
ht-degree: 100%

---

# 選擇加入使用案例 {#opt-in-use-cases}

管理選擇加入服務的使用案例與解決方案範例。

## 提示與疑難排解 {#section-5c566366410f4a8f89eca0d3f556d99f}

* 訪客 JS initialize 會在頁面載入期間同步及執行。如果您正在與 CMP 或具有高延遲的權限持續性連接，最好使用 [選擇加入設定](../../implementation-guides/opt-in-service/getting-started.md#section-cf9ab638780141c9b62dc57cf00b7047) 中所述的非同步函數。
* 選擇加入是根據網域而定的實作。它將不會處理跨網域的實作。
* 若要針對特定程式庫停用第三方呼叫，您需要分別在每個程式庫中設定該偏好設定。

## 選擇加入情境 {#section-1178053c065c430bba26f82ef383a71c}

以下使用案例為使用選擇加入服務的想法範例。

<table id="table_83C85343611344D8A8315157C1B4240F"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> 需求 </th> 
   <th colname="col2" class="entry"> 解決方案 </th> 
   <th colname="col3" class="entry"> 影響 </th> 
  </tr>
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p>可以在同意之前收集 Analytics，但只有在獲得同意後才可載入所有其他程式庫 </p> </td> 
   <td colname="col2"> <p>使用選擇加入在同意前啟用 Analytics 類別 </p> </td> 
   <td colname="col3"> <p>Analytics 會使用 Analytics 識別碼，而不是在同意前所收集的 ECID。在核准 ECID 之後，將會使用新的識別碼，而且訪客將會收到可用於啟用和整合的 ECID。 </p> <p>訪客應按照同意前/同意後分段。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>在同意前可以收集第一方測量。在收到同意之前避免使用所有其他類型的資料。 </p> </td> 
   <td colname="col2"> <p>使用選擇加入在同意前啟用 Analytics + ECID 程式庫。 </p> <p>新增 ‘disablethirdpartycookies’ 設定到 ECID 程式庫可在同意前封鎖第三方 Cookie + ID 同步。 </p> </td> 
   <td colname="col3"> <p>Adobe Demdex 呼叫將會觸發 ECID 擷取，但不會有任何 Demdex Cookie、其他第三方 Cookie 或 ID 同步。 </p> <p>對於 Analytics，確保訪客在同意前/同意後保持一致。同意前的收集將與同意後的資料收集相繫結。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>在同意前可接受第一方測量及目標定位。在收到同意之前避免使用所有其他類型的資料。 </p> </td> 
   <td colname="col2"> <p>使用選擇加入在同意前啟用 Analytics + ECID + Target 程式庫。 </p> <p>在 ECID 程式庫中新增 <span class="codeph">isablethirdpartycookies</span> 設定，以在預先同意狀態下封鎖第三方 Cookie 和 ID 同步。移除同意後狀態下的標幟。 </p> </td> 
   <td colname="col3"> <p>Adobe Demdex 呼叫將會觸發 ECID 擷取，但不會有任何 Demdex Cookie、其他第三方 Cookie 或 ID 同步。 </p> <p>對於第一方解決方案，確保訪客在同意前/同意後保持一致。同意前的收集將與同意後的資料收集相繫結。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>不允許在同意前狀態下設定任何 Cookie </p> </td> 
   <td colname="col2"> <p>在收到同意之前使用選擇加入可避免所有程式庫載入 </p> </td> 
   <td colname="col3"> <p>實作如預期般運作，而且所有程式庫 (包括 ECID) 將會在同意後載入正確序列中。 </p> <p>從未同意被追蹤的客戶會遇到資料遺失狀況。 </p> </td> 
  </tr> 
 </tbody> 
</table>
