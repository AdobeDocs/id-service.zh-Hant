---
description: 瀏覽器使用跨原始資源共用 (CORS) 來從目前網域以外的其他網域要求資源。Experience Cloud Identity Service 支援 CORS 標準，以允許這些用戶端的跨原始資源要求。此 ID 服務在舊版瀏覽器或不支援 CORS 的瀏覽器上會回復為 JSONP 要求。
keywords: ID 服務
title: Experience Cloud Identity Service 的 CORS 支援
exl-id: 0e8ffe85-8d1f-42a0-aae3-a2b3b28c7bce
source-git-commit: 06e935a4ba4776baa900d3dc91e294c92b873c0f
workflow-type: tm+mt
source-wordcount: '609'
ht-degree: 96%

---

# Experience Cloud Identity 服務的 CORS 支援 {#cors-support-in-the-experience-cloud-id-service}

瀏覽器使用跨原始資源共用 (CORS) 來從目前網域以外的其他網域要求資源。Experience Cloud Identity Service 支援 CORS 標準，以允許這些用戶端的跨原始資源要求。此 ID 服務在舊版瀏覽器或不支援 CORS 的瀏覽器上會回復為 JSONP 要求。

## 相同來源政策和ID服務要求的問題 {#section-6608cf46d27143eeaeabacaa6aa14e8e}

相同來源政策是網頁瀏覽器實作的安全控制或限制。在此層級實作時，網頁瀏覽器會自行判斷是否應允許或是封鎖從一個頁面向另一個頁面提出的資源要求。要了判斷某個要求是否為相同來源的要求，瀏覽器會比較：

* 統一資源識別項 (URI)
* 主機名稱 (例如 http://www.my-webpage-example.com)
* 連接埠號碼 (例如，適用於 HTTP 和 HTTPS 要求的連接埠 80 和 440)

如果兩個頁面具有相同特性，瀏覽器會讓要求成功，如果不具有相同特性則會封鎖資源要求。

## CORS會根據相同來源原則解決問題 {#section-76c87ec3295d447bab220c84f138c235}

CORS 提供安全、有效的方法在不同網域中要求資源。CORS 規格包括瀏覽器用來傳送、接收及評估資源要求的一組 HTTP 標頭。評估資源要求稱為 *`preflight check`*。這項檢查可讓瀏覽器和伺服器判斷要允許或封鎖哪些要求。此預檢對應用程式、API 或要求資源的指令碼而言是透明的。資源要求處理中有兩個重要的標頭，包括：

* `Origin`：識別要求來源的要求標頭。
* `Access-Control-Allow-Origin`：指出資源是否可與要求者共用的回應標頭。

讓我們來看看這些標題如何運作。在此範例中，假設有一家金融服務公司已在其網站 www.finance-website.com. 上實作 [!DNL Experience Cloud] ID 服務。下表定義了 CORS 要求和回應標頭如何檢查對資源的存取權。

<table id="table_B004ACF52B5A4D33B1DCF7EA77BE4E6D"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> 動作 </th> 
   <th colname="col2" class="entry"> 說明 </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <b>要求</b> </p> </td> 
   <td colname="col2"> <p>當金融公司頁面載入時，瀏覽器會向 <span class="codeph">dpm.demdex.net</span> 提出要求。這是對 ID 服務所使用的資料收集伺服器 (DCS) 網域的呼叫。這個跨網域要求包含此標頭： </p> <p> 
     <ul class="simplelist"> 
      <li> <span class="codeph"> Origin:https://www.finance-website.com</span> </li> 
     </ul> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>回應</b> </p> </td> 
   <td colname="col2"> <p>來自 DCS 網域的回應包括這些標頭，它們可授予此金融公司網站對所需資源的存取權： </p> <p> 
     <ul class="simplelist"> 
      <li> <span class="codeph"> Access-Control-Allow-Origin: https://www.finance-website.com</span> </li> 
      <li> <span class="codeph"> Access-Control-Allow-Credentials: true</span> </li> 
     </ul> </p> </td> 
  </tr> 
 </tbody> 
</table>

另請參閱 [useCORSOnly](../library/function-vars/use-cors-only.md#reference-8a9a143d838b48d6b23329b84b13e1fa)。

## 使用CORS的其他好處 {#section-6f44f30694c44f95bf9854b8a2af8449}

下表探討了 CORS 為使用 ID 服務的客戶提供的一些優點。

<table id="table_AEB51A263D454F90B66E8C8D0513CF79"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> 優點 </th> 
   <th colname="col2" class="entry"> 說明 </th> 
  </tr>
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p><b>提升安全性</b> </p> </td> 
   <td colname="col2"> <p>CORS 會使用 <a href="https://developer.mozilla.org/zh-TW/docs/Web/API/XMLHttpRequest" format="https" scope="external"> XMLHttpRequest</a> 來要求及傳輸資料。這個方法比 JSONP 要求更安全。它可確保沒有方法可執行任何 JavaScript (來自 DCS 的回應中可能會包含 JavaScript)。CORS XMLHttpRequest 要求裝載會由 ID 服務 JavaScript 剖析，而不只會在回呼函數中呼叫。 </p> <p> <p>注意：為了接受 Cookie，<span class="codeph">XMLHttpRequest</span> 物件的 <span class="codeph">withCredentials</span> 屬性必須設定為 <span class="codeph">true</span>。Chrome、Firefox、Internet Explorer (v10+)、Opera 和 Safari 都支援這個屬性。 </p> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p><b>效能改良</b> </p> </td> 
   <td colname="col2"> <p>CORS 基於以下原因有助於改善效能： </p> 
    <ul id="ul_EC3A178003A94D70883B914050D7C464"> 
     <li id="li_F8B44352BFBB46CDBD07AE40B9F2D0EC">瀏覽器會管理資源要求。要求處理對 ID 服務而言是透明的。 </li> 
     <li id="li_C63E43A4CAB84210AB6A39100E5864BE">不同於非同步 JSONP 要求，瀏覽器不會取消 CORS 要求的優先順序並將其排入佇列。 </li> 
     <li id="li_1A2A15F591B84D1BAED3CFAB391EEBEC">ID 服務會在容許的程度內進行回應。這表示當以 <span class="codeph">Origin</span> 傳入 URL 時，ID 服務會授予必要資源的頁面存取權限。 </li> 
    </ul> </td> 
  </tr> 
 </tbody> 
</table>
