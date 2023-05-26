---
description: 概述 Experience Cloud Identity Service 搭配舊有 Analytics ID 之使用方式。
keywords: ID 服務
title: Analytics 與 Experience Cloud ID 請求
exl-id: 8c682159-e23a-4641-9ffd-e0028dc2f305
source-git-commit: cb89ac70e37f35d5e4e2b971f2df9645304522f8
workflow-type: tm+mt
source-wordcount: '444'
ht-degree: 100%

---

# Analytics 與 Experience Cloud ID 請求{#analytics-and-experience-cloud-id-requests}

概述 Experience Cloud Identity Service 搭配舊有 Analytics ID 之使用方式。

## 摘要 {#section-64d8523ff7634cb987d0c6480f587dd3}

過去，Experience Cloud Identity Service 即已緊密整合至 Adobe Analytics。除了保有 Analytics 的完整，現在也可執行 [!DNL Experience Cloud] 中其他解決方案和功能的重要功能。由於過去的這個舊有特色，檢查或寫入 Analytics ID 的方式與 [Experience Cloud Identity Service 如何要求與設定 ID...](../../introduction/id-request.md#concept-2caacebb1d244402816760e9b8bcef6a) 中說明的一般程序略有不同。如需深入了解檢查 ID 的作業順序，請參閱[設定 Analytics 與 Experience Cloud ID](../../reference/analytics-reference/analytics-ids.md#concept-f381dd18ee184c6c8e48286937a161d6)。

## 未在瀏覽器中設定 AMCV Cookie {#section-cccf10cd775e4a95a7e98d3c3c0ff9a9}

如果 [!DNL Experience Cloud] (AMCV) Cookie 不存在，您撥打 [!DNL Adobe] 的 ID 服務電話時，得到的回應會依據您是否擁有舊版 Analytics ID 而有所不同。舊版 [!DNL Analytics] ID 會儲存在 [s_vi Cookie](https://experienceleague.adobe.com/docs/core-services/interface/ec-cookies/cookies-analytics.html?lang=zh-Hant) 中。下表說明系統會如何根據 s_vi Cookie 的狀態，將 ID 覆寫至 AMCV Cookie。

<table id="table_DC85FECE26DD424E841BA1059AF1E57F"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> s_vi Cookie 狀態 </th> 
   <th colname="col2" class="entry"> 說明 </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <b>s_vi Cookie 未設定</b> </p> </td> 
   <td colname="col2"> <p>ID 服務為訪客指派一個 <span class="keyword">Experience Cloud</span> ID (MID)。MID 可在 <span class="keyword">Analytics</span> 和其他 <span class="keyword">Experience Cloud</span> 解決方案中識別訪客。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>已設定 s_vi Cookie</b> </p> </td> 
   <td colname="col2"> <p>擁有 s_vi Cookie 的網站訪客首次遇到 Experience Cloud Identity Service 時，此服務會: </p> 
    <ul id="ul_BE584810280D4874AF802A9247011787"> 
     <li id="li_AA395B09A3174AF78F3EC10053E2E4F5">將儲存在 s_vi Cookie 中的 <span class="keyword">Analytics</span> ID 寫入 AMCV Cookie。這會寫入成為 <span class="keyword">Analytics</span> ID (AID)。此動作<i>不會</i>影響訪客計數。<span class="keyword">Analytics</span> 將繼續使用舊有 ID 識別用戶。 </li> 
     <li id="li_8735DE21FEA542BA8024109B8FE1E2ED">將 MID 寫入至 AMCV Cookie。MID 可跨不同的解決方案識別用戶。 </li> 
    </ul> <p> <p>注意：若使用<a href="../../reference/analytics-reference/grace-period.md" format="dita" scope="local">寬限期</a>，資料中心回應一律會包含儲存在 s_vi Cookie 中的舊有 ID。在寬限期期間，舊有 ID 會寫入 AMCV Cookie 為 AID 值。 </p> </p> </td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>s_fid Cookie 所識別的用戶不會將其舊有的 FID 值移轉到 AMCV Cookie。有了 s_fid Cookie，用戶移轉時會如同 s_vi Cookie 不存在 (請參閱上述說明)，就像是全新訪客造訪您的網站。如需詳細資訊，請參閱 [Analytics Cookie](https://experienceleague.adobe.com/docs/core-services/interface/ec-cookies/cookies-analytics.html?lang=zh-Hant)。

## 已在瀏覽器中設定 AMCV Cookie {#section-01c088fc565c4b24ba1722c7cc240310}

如果 AMCV Cookie 已存在， 將使用 MID 作為 [!DNL Analytics] 識別碼 (假設 Cookie 中沒有舊有的 [!DNL Analytics]Analytics ID 值)。
