---
description: 瀏覽器使用跨原始資源共用 (CORS) 來從目前網域以外的其他網域要求資源。Experience Cloud Identity 服務支援 CORS 標準，以允許這些用戶端的跨原始資源要求。此 ID 服務在舊版瀏覽器或不支援 CORS 的瀏覽器上會回復為 JSONP 要求。
keywords: ID Service
seo-description: 瀏覽器使用跨原始資源共用 (CORS) 來從目前網域以外的其他網域要求資源。Experience Cloud Identity 服務支援 CORS 標準，以允許這些用戶端的跨原始資源要求。此 ID 服務在舊版瀏覽器或不支援 CORS 的瀏覽器上會回復為 JSONP 要求。
seo-title: Experience Cloud Identity 服務的 CORS 支援
title: Experience Cloud Identity 服務的 CORS 支援
uuid: e656b573-72a8-4312-a7d5-5cc3818f0a9e
translation-type: tm+mt
source-git-commit: e6d65f1bfed187d7440512e8f3c2de0550506c95
workflow-type: tm+mt
source-wordcount: '672'
ht-degree: 52%

---


# Experience Cloud Identity 服務的 CORS 支援 {#cors-support-in-the-experience-cloud-id-service}

瀏覽器使用跨原始資源共用 (CORS) 來從目前網域以外的其他網域要求資源。Experience Cloud Identity 服務支援 CORS 標準，以允許這些用戶端的跨原始資源要求。此 ID 服務在舊版瀏覽器或不支援 CORS 的瀏覽器上會回復為 JSONP 要求。

## 相同來源政策和 ID 服務要求的問題 {#section-6608cf46d27143eeaeabacaa6aa14e8e}

相同來源政策是網頁瀏覽器實作的安全控制或限制。在此層級實作時，網頁瀏覽器會自行判斷是否應允許或是封鎖從一個頁面向另一個頁面提出的資源要求。若要判斷請求是否為相同來源請求，瀏覽器會比較：

* 統一資源標識符(URI)
* 主機名(例如http://www.my-webpage-example.com)
* 埠號（例如，HTTP和HTTPS請求的埠80和440）

如果兩個頁面都有這些特性，瀏覽器允許請求成功，如果它們不共用，則阻止資源請求。

## CORS可解決相同來源原則的問題 {#section-76c87ec3295d447bab220c84f138c235}

CORS提供安全、有效的方式，跨不同網域要求資源。 CORS規格包含一組HTTP標題，瀏覽器用來傳送、接收和評估資源要求。 評估資源請求稱為 *`preflight check`*。 此檢查可讓瀏覽器和伺服器判斷允許或封鎖哪些要求。 預檢檢查對要求資源的應用程式、API或指令碼是透明的。 資源請求流程中兩個重要的標題包括：

* `Origin`: 識別要求來源的要求標題。
* `Access-Control-Allow-Origin`: 指出資源是否可與要求者共用的回應標題。

讓我們來看看這些標題如何運作。在此範例中，假設有一家金融服務公司已在其網站上實作 [!DNL Experience Cloud] ID 服務: www.finance-website.com 。下表定義CORS要求和回應標題檢查資源存取權的方式。

<table id="table_B004ACF52B5A4D33B1DCF7EA77BE4E6D"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> 動作 </th> 
   <th colname="col2" class="entry"> 說明 </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <b>請求</b> </p> </td> 
   <td colname="col2"> <p>當金融公司頁面載入時，瀏覽器會向 <span class="codeph">dpm.demdex.net</span> 提出要求。這是對ID服務所使用資料收集伺服器(DCS)網域的呼叫。 此跨網域請求包含標題： </p> <p> 
     <ul class="simplelist"> 
      <li> <span class="codeph"> Origin:https://www.finance-website.com</span> </li> 
     </ul> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>回應</b> </p> </td> 
   <td colname="col2"> <p>來自DCS網域的回應包括這些標題，這些標題可讓財務公司的網站存取所需資源： </p> <p> 
     <ul class="simplelist"> 
      <li> <span class="codeph"> Access-Control-Allow-Origin: https://www.finance-website.com</span> </li> 
      <li> <span class="codeph"> Access-Control-Allow-Credentials: true</span> </li> 
     </ul> </p> </td> 
  </tr> 
 </tbody> 
</table>

另請參閱 [useCORSOnly](../library/function-vars/use-cors-only.md#reference-8a9a143d838b48d6b23329b84b13e1fa)。

## 使用 CORS 的其他好處 {#section-6f44f30694c44f95bf9854b8a2af8449}

下表說明CORS為使用ID服務的客戶提供的一些優點。

<table id="table_AEB51A263D454F90B66E8C8D0513CF79"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> 好處 </th> 
   <th colname="col2" class="entry"> 說明 </th> 
  </tr>
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p><b>提升安全性</b> </p> </td> 
   <td colname="col2"> <p>CORS使 <a href="https://developer.mozilla.org/zh-TW/docs/Web/API/XMLHttpRequest" format="https" scope="external"> 用XMLHttpRequest</a> ，來請求和傳輸資料。 此方法比JSONP請求更安全。 它可確保無法執行任意JavaScript，而DCS的回應中可能包含這些JavaScript。 CORS XMLHttpRequest回應裝載由ID服務JavaScript解析，而非簡單地在回呼函式中執行。 </p> <p> <p>注意: 為了接受 Cookie，<span class="codeph">XMLHttpRequest</span> 物件的 <span class="codeph">withCredentials</span> 屬性必須設定為 <span class="codeph">true</span>。Chrome、Firefox、Internet Explorer(v10+)、Opera和Safari都支援此屬性。 </p> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p><b>效能改進</b> </p> </td> 
   <td colname="col2"> <p>CORS有助於改善效能，因為： </p> 
    <ul id="ul_EC3A178003A94D70883B914050D7C464"> 
     <li id="li_F8B44352BFBB46CDBD07AE40B9F2D0EC">瀏覽器管理資源請求。 請求程式對ID服務是透明的。 </li> 
     <li id="li_C63E43A4CAB84210AB6A39100E5864BE">與非同步JSONP請求不同，瀏覽器不會取消CORS請求的優先順序並將其排入佇列。 </li> 
     <li id="li_1A2A15F591B84D1BAED3CFAB391EEBEC">ID服務會以許可方式回應。 這表示當以 <span class="codeph">Origin</span> 傳入 URL 時，ID 服務會授予必要資源的頁面存取權限。 </li> 
    </ul> </td> 
  </tr> 
 </tbody> 
</table>

