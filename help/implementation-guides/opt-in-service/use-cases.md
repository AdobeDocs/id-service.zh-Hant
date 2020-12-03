---
description: 管理選擇加入服務的使用案例與解決方案範例。
seo-description: 管理選擇加入服務的使用案例與解決方案範例。
seo-title: 選擇加入使用案例
title: 選擇加入使用案例
uuid: d75a44d5-b713-43d1-b5b6-95d1d0d213a7
translation-type: tm+mt
source-git-commit: 0c300aa92991c0dec2ccdeeb34f9d886dcac7671
workflow-type: tm+mt
source-wordcount: '437'
ht-degree: 16%

---


# 選擇加入使用案例 {#opt-in-use-cases}

管理選擇加入服務的使用案例與解決方案範例。

## 提示與疑難排解 {#section-5c566366410f4a8f89eca0d3f556d99f}

* 訪客JS初始化是同步的，並在頁面載入期間執行。 如果您要與CMP或權限持久性進行介面，但延遲性較高，則最好使用「選擇加入設定」中介紹的 [非同步功能](../../implementation-guides/opt-in-service/getting-started.md#section-cf9ab638780141c9b62dc57cf00b7047)。
* 選擇加入是依網域實作。 它不會處理跨網域實施。
* 若要停用特定程式庫的協力廠商呼叫，您必須在每個程式庫中個別設定該偏好設定。

## 選擇加入藍本 {#section-1178053c065c430bba26f82ef383a71c}

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
   <td colname="col1"> <p>Analytics可在事先同意狀態下收集，但所有其他資料庫在收到同意前無法載入 </p> </td> 
   <td colname="col2"> <p>使用選擇加入以啟用預先同意狀態的Analytics類別 </p> </td> 
   <td colname="col3"> <p>Analytics會在事前同意收集中使用Analytics識別碼，而非ECID。 ECID核准後，將會使用新的識別碼，而訪客將會收到可用於啟動和整合的ECID。 </p> <p>預期訪客會在事前／事後同意狀態中分割。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>第一方測量可在事先同意狀態下收集。 所有其他類型的資料使用在獲得同意之前都無法使用。 </p> </td> 
   <td colname="col2"> <p>使用選擇加入可啟用Analytics + ECID程式庫的預先同意狀態。 </p> <p>將「disablethirdpartycookies」設定新增至ECID程式庫，以在事先同意狀態中封鎖第三方Cookie + ID同步 </p> </td> 
   <td colname="col3"> <p>Adobe Demdex呼叫會觸發ECID擷取，但不會出現Demdex Cookie、其他協力廠商Cookie或ID同步。 </p> <p>在Analytics的同意前／同意後狀態中，讓訪客保持一致。 在事先同意狀態下收集資料將系結至事先同意後收集的資料。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>在預先同意狀態下，第一方測量加上定位是可以接受的。 所有其他類型的資料使用在獲得同意之前都無法使用。 </p> </td> 
   <td colname="col2"> <p>使用選擇加入，啟用Analytics + ECID + Target程式庫的預先同意狀態。 </p> <p>在 ECID 資料庫中新增 <span class="codeph">isablethirdpartycookies</span> 設定，以在預先同意狀態下封鎖第三方 Cookie 和 ID 同步。移除許可後狀態的旗標。 </p> </td> 
   <td colname="col3"> <p>Adobe Demdex呼叫將觸發ECID擷取，但不會出現Demdex Cookie、其他第三方Cookie或ID同步。 </p> <p>在第一方解決方案的許可前／許可後狀態中，讓訪客保持一致。 在事先同意狀態下收集資料將系結至事先同意後收集的資料。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>不允許在預先同意狀態中設定Cookie </p> </td> 
   <td colname="col2"> <p>使用選擇加入功能，在收到同意前，封鎖所有程式庫 </p> </td> 
   <td colname="col3"> <p>實作如預期，所有資料庫（包括ECID）都會以正確順序載入許可後狀態。 </p> <p>從未同意被追蹤的客戶的資料遺失。 </p> </td> 
  </tr> 
 </tbody> 
</table>

