---
description: 管理選擇加入服務的使用案例與解決方案範例。
seo-description: 管理選擇加入服務的使用案例與解決方案範例。
seo-title: 選擇加入使用案例
title: 選擇加入使用案例
uuid: d75a44d5-b713-43d1-b5b6-95d1d0d213a7
translation-type: tm+mt
source-git-commit: 0c300aa92991c0dec2ccdeeb34f9d886dcac7671

---


# 選擇加入使用案例 {#opt-in-use-cases}

管理選擇加入服務的使用案例與解決方案範例。

## 提示與疑難排解 {#section-5c566366410f4a8f89eca0d3f556d99f}

* 訪客 JS 初始化為同步作業，會在頁面載入期間執行。如果您使用 CMP 或具有高延遲的權限持續性操作，最好使用[選擇加入設定](../../implementation-guides/opt-in-service/getting-started.md#section-cf9ab638780141c9b62dc57cf00b7047)中說明的非同步函數。
* 選擇加入是按各網域的實作。不會處理跨網域的實作。
* 若要停用特定資料庫的第三方呼叫，您需要分別在各資料庫中設定此偏好設定。

## 選擇加入案例 {#section-1178053c065c430bba26f82ef383a71c}

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
   <td colname="col1"> <p>Analytics 可以在預先同意狀態下收集，但在收到同意前，所有其他資料庫無法載入 </p> </td> 
   <td colname="col2"> <p>使用選擇加入以在預先同意狀態下啟用 Analytics 類別 </p> </td> 
   <td colname="col3"> <p>Analytics 會使用 Analytics 識別碼而非 ECID 來收集預先同意。ECID 通過核准後，系統會使用新的識別碼，且訪客會收到 ECID，可用來啟動和整合。 </p> <p>訪客在預先/事後同意狀態下可能會有分散的情形。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>第一方度量可以在預先同意狀態下收集。在收到同意前，所有其他類型的資料使用皆無法使用。 </p> </td> 
   <td colname="col2"> <p>使用選擇加入以在預先同意狀態下啟用 Analytics 與 ECID 資料庫。 </p> <p>在 ECID 資料庫中新增「disablethirdpartycookies」設定，以在預先同意狀態下封鎖第三方 Cookie 和 ID 同步 </p> </td> 
   <td colname="col3"> <p>Adobe Demdex 會觸發 ECID 擷取，但 Demdex Cookie、其他第三方 Cookie 或 ID 同步不會出現。 </p> <p>在預先/事後同意狀態下，為 Analytics 保持訪客一致。在預先同意狀態下收集，會與事後同意資料收集繫結。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>在預先同意狀態下，可接受第一方度量與目標鎖定。在收到同意前，所有其他類型的資料使用皆無法使用。 </p> </td> 
   <td colname="col2"> <p>使用選擇加入以在預先同意狀態下啟用 Analytics、ECID 與 Target 資料庫。 </p> <p>在 ECID 資料庫中新增 <span class="codeph">isablethirdpartycookies</span> 設定，以在預先同意狀態下封鎖第三方 Cookie 和 ID 同步。在事後同意狀態下移除標幟。 </p> </td> 
   <td colname="col3"> <p>Adobe Demdex 會觸發 ECID 擷取，但 Demdex Cookie、其他第三方 Cookie 或 ID 同步不會出現。 </p> <p>在預先/事後同意狀態下為第一方解決方案保持訪客一致。在預先同意狀態下收集，會與事後同意資料收集繫結。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>不允許在預先同意狀態下設定任何 Cookie </p> </td> 
   <td colname="col2"> <p>使用選擇加入來封鎖資料庫載入，直到收到同意。 </p> </td> 
   <td colname="col3"> <p>在事後同意狀態下，實作可順利運作，且包括 ECID 在內的所有資料庫會以正確順序載入。 </p> <p>從未同意追蹤的客戶發生資料遺失情形。 </p> </td> 
  </tr> 
 </tbody> 
</table>

