---
description: 內容安全性原則(CSP)是HTTP標題和安全性功能，可讓瀏覽器控制載入網頁的資源類型。 如果您使用ID服務並有嚴格的CSP，且使用白名單來接受來自受信任網域的資源，請檢閱本節。 您需要將此處列出的Adobe網域新增至CSP白名單。
keywords: ID Service
seo-description: 內容安全性原則(CSP)是HTTP標題和安全性功能，可讓瀏覽器控制載入網頁的資源類型。 如果您使用ID服務並有嚴格的CSP，且使用白名單來接受來自受信任網域的資源，請檢閱本節。 您需要將此處列出的Adobe網域新增至CSP白名單。
seo-title: 內容安全性原則及 Experience Cloud Identity 服務
title: 內容安全性原則及 Experience Cloud Identity 服務
uuid: 7399edf3-01c1-4730-834e-e2dd2c5791ff
translation-type: tm+mt
source-git-commit: d2bc0e7fedc4e48d51f5dad158f9f8bfcb0cb4f3

---


# 內容安全性原則及 Experience Cloud Identity 服務{#content-security-policies-and-the-experience-cloud-id-service}

內容安全性原則(CSP)是HTTP標題和安全性功能，可讓瀏覽器控制載入網頁的資源類型。 如果您使用ID服務並有嚴格的CSP，且使用白名單來接受來自受信任網域的資源，請檢閱本節。 您需要將此處列出的Adobe網域新增至CSP白名單。

## CSP 檢視  {#section-5fde5c00a678455c914b8307a8caab82}

CSP 會利用 HTTP 標頭 `Content-Security-Policy` 來控制瀏覽器要接受或在網頁中要載入的資源類型。套用 CSP 能協助您避免以下情形：

* 如果來源未知或未包含在白名單中，則無法載入JavaScript檔案。
* 跨網站指令碼(XXS)攻擊。
* 資料注入攻擊。
* 網站毀損攻擊。
* 惡意軟體散發。

CSP的使用是常見的，也是眾所周知的。 本檔案並非詳細說明CSP的目的（如需詳細資訊，請參閱下列相關資訊連結）。 重要的是，您瞭解如果您使用這些網域名稱，並有嚴格的安全性政策，您應將哪些Adobe網域名稱新增至CSP。 新增這些網域可讓存取您網站的訪客瀏覽器，對您使用的Experience Cloud資源進行重要呼叫。

## 加入白名單的 Experience Cloud 網域 {#section-30693e9a96834edfbf04de9e698cf2aa}

將這些網域名稱或URL新增至CSP，以取得您所使用之每個Experience Cloud解決方案或服務清單。

<table id="table_EC9FC999A62D4B7A830CE73B0AB9EF3C"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Experience Cloud解決方案或服務 </th> 
   <th colname="col2" class="entry"> 說明 </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <b>AppMeasurement</b> </p> </td> 
   <td colname="col2"> <p>修改您的 CSP 以包含以下項目： </p> <p> 
     <ul id="ul_7522AE83A03A4115A84DF5B32D6DD79B"> 
      <li id="li_AB1EC161FB154BEDA1BEFE76C8A38A90"> <span class="codeph"> *.2o7.net</span> </li> 
      <li id="li_4B12A283716746949201528CD6AF529E"> <span class="codeph"> *.omtrdc.net</span> </li> 
     </ul> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>Target</b> </p> </td> 
   <td colname="col2"> <p>修改您的 CSP 以包含 <span class="codeph">*.tt.omtrdc.net</span>。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>Experience Cloud ID 服務與 Audience Manager</b> </p> </td> 
   <td colname="col2"> <p>修改 CSP 以納入以下網域。</p> 
   <p><ul>
   <li>connect-src 'self' <code>https://*.demdex.net https://cm.everesttech.net https://assets.adobedtm.com;</code></li>
   <li>img-src 'self' <code>https://*.demdex.net https://cm.everesttech.net https://assets.adobedtm.com;</code></li>
   <li>script-src 'self' <code>https://*.demdex.net https://cm.everesttech.net https://assets.adobedtm.com;</code></li>
   <li>frame-src 'self' <code>https://*.demdex.net;</code></li>
   <li>如果您是使用 Adobe Launch 部署標籤，也請將 <code>https://assets.adobedtm.com</code> 新增至網域清單。</li></ul></p> <p>對 <span class="codeph">demdex.net</span> 網域發出的呼叫用於產生 <a href="../introduction/cookies.md" format="dita" scope="local">Cookie 與 Experience Cloud Identity 服務</a>及用於 ID 同步。亦請參閱<a href="https://docs.adobe.com/content/help/zh-Hant/audience-manager/user-guide/reference/demdex-calls.html" format="https" scope="external">瞭解向 Demdex 網域進行的呼叫</a>。 </p> </td> </tr> 
 <tr>
 <td colname="col1"> <p> <b>Activity Map 增效模組</b> </p> </td> 
 <td colname="col2"> <p>修改您的 CSP 以包含 *.adobe.com。**注意**：如果您在 2020 年 1 日前即已安裝 Activity Map，您的瀏覽器仍會收到 *.omniture.com 的原始請求，但會將其重新導向 *.adobe.com。 </p></td> 
 </tr>
 </tbody> 
</table>

>[!MORELIKETHIS]
>* [內容安全性原則參考](https://content-security-policy.com/)
>* [MDN：內容安全性原則](https://developer.mozilla.org/zh-TW/docs/Web/HTTP/CSP)
>* [Wikipedia：內容安全性原則](https://en.wikipedia.org/wiki/Content_Security_Policy)

