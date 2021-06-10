---
description: 內容安全性原則 (CSP) 是 HTTP 標題和安全性功能，可讓瀏覽器控制要在網頁上載入的資源類型。如果您使用 ID 服務，且具備使用白名單接受來自受信任網域之資源的嚴格 CSP，請詳閱本節。您必須將此處所列的 Adobe 網域新增至 CSP 白名單。
keywords: ID 服務
title: 內容安全性原則及 Experience Cloud Identity Service
exl-id: e35c6809-764e-4c3e-9139-88bb92e82338
source-git-commit: cb89ac70e37f35d5e4e2b971f2df9645304522f8
workflow-type: tm+mt
source-wordcount: '547'
ht-degree: 100%

---

# 內容安全性原則及 Experience Cloud Identity Service{#content-security-policies-and-the-experience-cloud-id-service}

內容安全性原則 (CSP) 是 HTTP 標題和安全性功能，可讓瀏覽器控制要在網頁上載入的資源類型。如果您使用 ID 服務，且具備使用白名單接受來自受信任網域之資源的嚴格 CSP，請詳閱本節。您必須將此處所列的 Adobe 網域新增至 CSP 白名單。

## CSP 檢視  {#section-5fde5c00a678455c914b8307a8caab82}

CSP 會利用 HTTP 標頭 `Content-Security-Policy` 來控制瀏覽器要接受或在網頁中要載入的資源類型。套用 CSP 能協助您避免以下情形：

* 在來源不明或未包含在白名單中的情況下載入 JavaScript 檔案。
* 跨網站指令碼 (XXS) 攻擊。
* 資料插入攻擊。
* 網站損毀攻擊。
* 惡意軟體散發。

CSP 的使用十分常見，且眾所周知。本文件的目的並非詳細說明 CSP (如需詳細資訊，請參閱下方連結中的相關資訊)。重要的是，您必須了解您在使用時應將何種 Adobe 網域名稱新增至 CSP，並擬定嚴格的安全性原則。新增這些網域，可讓存取您的網站的訪客瀏覽器能夠對您使用的 Experience Cloud 資源進行重要呼叫。

## 加入白名單的 Experience Cloud 網域 {#section-30693e9a96834edfbf04de9e698cf2aa}

針對您所使用的每個 Experience Cloud 解決方案或服務，請將下列網域名稱或 URL 新增至您的 CSP。

<table id="table_EC9FC999A62D4B7A830CE73B0AB9EF3C"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Experience Cloud 解決方案或服務 </th> 
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
   <li>如果您是使用 Adobe Launch 部署標籤，也請將 <code>https://assets.adobedtm.com</code> 新增至網域清單。</li></ul></p> <p>對 <span class="codeph">demdex.net</span> 網域發出的呼叫用於產生 <a href="../introduction/cookies.md" format="dita" scope="local">Cookie 與 Experience Cloud Identity Service</a> 及用於 ID 同步。亦請參閱<a href="https://experienceleague.adobe.com/docs/audience-manager/user-guide/reference/demdex-calls.html?lang=zh-Hant" format="https" scope="external">了解向 Demdex 網域進行的呼叫</a>。 </p> </td> </tr> 
 <tr>
 <td colname="col1"> <p> <b>Activity Map 增效模組</b> </p> </td> 
 <td colname="col2"> <p>修改您的 CSP 以包含 *.adobe.com。**注意**：如果您在 2020 年 1 日前即已安裝 Activity Map，您的瀏覽器仍會收到 *.omniture.com 的原始請求，但會將其重新導向 *.adobe.com。 </p></td> 
 </tr>
 <tr>
 <td colname="col1"> <p> <b>Advertising Analytics</b> </p> </td> 
 <td colname="col2"> <p>如果您對查詢字串參數有控制權，請務必將 `s_kwcid` 和 `ef_id` 參數列入白名單。就技術而言，Advertising Analytics 僅會使用 `s_kwcid`，但如果您取得 Ad Cloud Search 或 DSP，系統也會使用 `ef_id`。這些查詢字串參數均為英數字元。`s_kwcid` 參數會使用「!」字元，而 `ef_id` 參數會使用「:」字元。如果您禁止在 URL 中使用「!」字元，您也需要將其列入白名單。</p></td> 
 </tr>
 </tbody> 
</table>

>[!MORELIKETHIS]
>
>* [內容安全性原則參考](https://content-security-policy.com/)
>* [MDN：內容安全性原則](https://developer.mozilla.org/zh-TW/docs/Web/HTTP/CSP)
>* [Wikipedia：內容安全性原則](https://en.wikipedia.org/wiki/Content_Security_Policy)

