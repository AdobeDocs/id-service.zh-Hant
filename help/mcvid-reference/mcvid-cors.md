---
description: 瀏覽器使用跨原始資源共用 (CORS) 來從目前網域以外的其他網域要求資源。Experience Cloud ID 服務支援 CORS 標準，以允許這些用戶端的跨原始資源要求。此 ID 服務在舊版瀏覽器或不支援 CORS 的瀏覽器上會回復為 JSONP 要求。
keywords: ID 服務
seo-description: 瀏覽器使用跨原始資源共用 (CORS) 來從目前網域以外的其他網域要求資源。Experience Cloud ID 服務支援 CORS 標準，以允許這些用戶端的跨原始資源要求。此 ID 服務在舊版瀏覽器或不支援 CORS 的瀏覽器上會回復為 JSONP 要求。
seo-title: Experience Cloud ID 服務的 CORS 支援
title: Experience Cloud ID 服務的 CORS 支援
uuid: e656b573-72a8-4312-a7d5-5cc3818f0a9e
translation-type: ht
source-git-commit: bb687c1cd14aae7faef2565dcf9d041a1c06e3bd

---


# Experience Cloud ID 服務的 CORS 支援 {#cors-support-in-the-experience-cloud-id-service}

瀏覽器使用跨原始資源共用 (CORS) 來從目前網域以外的其他網域要求資源。Experience Cloud ID 服務支援 CORS 標準，以允許這些用戶端的跨原始資源要求。此 ID 服務在舊版瀏覽器或不支援 CORS 的瀏覽器上會回復為 JSONP 要求。

## 相同來源政策和 ID 服務要求的問題 {#section-6608cf46d27143eeaeabacaa6aa14e8e}

相同來源政策是網頁瀏覽器實施的安全控制或限制。在此層級實施時，網頁瀏覽器會自行判斷是否應允許或是封鎖從一個頁面向另一個頁面提出的資源要求。為了判斷某個要求是否為相同來源要求，瀏覽器會比較:

* 統一資源識別碼 (URI)
* 主機名稱 (例如 http://www.my-webpage-example.com)
* 連接埠號碼 (例如連接埠 80 和 440 用於 HTTP 和 HTTPS 要求)

如果兩個頁面共用這些特性則瀏覽器會允許要求，若不共用則封鎖資源要求。

## CORS 可解決相同來源政策的問題{#section-76c87ec3295d447bab220c84f138c235}

CORS 提供在不同網域間要求資源的安全、有效方法。CORS 規格包含一組 HTTP 標題，供瀏覽器用來傳送、接收和評估資源要求。評估資源要求稱為*`preflight check`*。這項檢查可讓瀏覽器和伺服器判斷應允許或是封鎖哪些要求。預檢檢查對於要求資源的應用程式、API 或指令檔是透明的。資源要求程序中有兩個很重要的標題:

* `Origin`: 識別要求來源的要求標題。
* `Access-Control-Allow-Origin`: 指出資源是否可與要求者共用的回應標題。

讓我們來看看這些標題如何運作。在此範例中，假設有一家金融服務公司已在其網站上實施 [!DNL Experience Cloud] ID 服務: www.finance-website.com。下表定義 CORS 要求和回應標題如何檢查資源的存取權限。

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
   <td colname="col2"> <p>當金融公司頁面載入時，瀏覽器會向 <span class="codeph">dpm.demdex.net</span> 提出要求。這是對 ID 服務所用資料收集伺服器 (DCS) 的網域提出的呼叫。此跨網域要求包含標題: </p> <p> 
     <ul class="simplelist"> 
      <li> <span class="codeph"> Origin:https://www.finance-website.com</span> </li> 
     </ul> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>回應</b> </p> </td> 
   <td colname="col2"> <p>來自 DCS 網域的回應包含這些標題，提供金融公司網站對所需資源的存取權限: </p> <p> 
     <ul class="simplelist"> 
      <li> <span class="codeph"> Access-Control-Allow-Origin: https://www.finance-website.com</span> </li> 
      <li> <span class="codeph"> Access-Control-Allow-Credentials: true</span> </li> 
     </ul> </p> </td> 
  </tr> 
 </tbody> 
</table>

另請參閱 [useCORSOnly](../mcvid-library/mcvid-function-vars/mcvid-use-cors-only.md#reference-8a9a143d838b48d6b23329b84b13e1fa)。

## 使用 CORS 的其他好處 {#section-6f44f30694c44f95bf9854b8a2af8449}

下表說明 CORS 能提供給使用 ID 服務之客戶的一些益處。

<table id="table_AEB51A263D454F90B66E8C8D0513CF79"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> 好處 </th> 
   <th colname="col2" class="entry"> 說明 </th> 
  </tr>
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p><b>提高安全性</b> </p> </td> 
   <td colname="col2"> <p>CORS 使用 <a href="https://developer.mozilla.org/zh-TW/docs/Web/API/XMLHttpRequest" format="https" scope="external"> XMLHttpRequest</a> 來要求與傳輸資料。此方法比 JSONP 要求更安全。它可確保絕對無法執行 DCS 回應中可能包含的任意 JavaScript。CORS XMLHttpRequest 回應裝載是由 ID 服務 JavaScript 剖析，不是單純在回撥函數中執行。 </p> <p> <p>注意: 為了接受 Cookie，<span class="codeph">XMLHttpRequest</span> 物件的 <span class="codeph">withCredentials</span> 屬性必須設定為 <span class="codeph">true</span>。Chrome、Firefox、Internet Explorer (10 以上版本)、Opera 和 Safari 都支援此屬性。 </p> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p><b>改進效能</b> </p> </td> 
   <td colname="col2"> <p>由於以下原因，CORS 有助於改進效能: </p> 
    <ul id="ul_EC3A178003A94D70883B914050D7C464"> 
     <li id="li_F8B44352BFBB46CDBD07AE40B9F2D0EC">由瀏覽器管理資源要求。要求過程對 ID 服務是透明的。 </li> 
     <li id="li_C63E43A4CAB84210AB6A39100E5864BE">不同於非同步 JSONP 要求，瀏覽器不會取消優先順序並將 CORS 要求排入佇列。 </li> 
     <li id="li_1A2A15F591B84D1BAED3CFAB391EEBEC">ID 服務會以許可方式回應。這表示當以 <span class="codeph">Origin</span> 傳入 URL 時，ID 服務會授予必要資源的頁面存取權限。 </li> 
    </ul> </td> 
  </tr> 
 </tbody> 
</table>

