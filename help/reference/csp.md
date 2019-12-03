---
description: 內容安全性原則 (CSP) 是一項 HTTP 標題和安全性功能，能讓瀏覽器控制要在網頁中載入的資源類型。如果您使用 ID 服務，且訂下嚴格的 CSP 以使用白名單來接受來自值得信賴網域的資料，請檢視本節的內容。您需要將此處所列的 Adobe 網域新增至您的 CSP 白名單中。
keywords: ID Service
seo-description: 內容安全性原則 (CSP) 是一項 HTTP 標題和安全性功能，能讓瀏覽器控制要在網頁中載入的資源類型。如果您使用 ID 服務，且訂下嚴格的 CSP 以使用白名單來接受來自值得信賴網域的資料，請檢視本節的內容。您需要將此處所列的 Adobe 網域新增至您的 CSP 白名單中。
seo-title: 內容安全性原則及 Experience Cloud Identity 服務
title: 內容安全性原則及 Experience Cloud Identity 服務
uuid: 7399edf3-01c1-4730-834e-e2dd2c5791ff
translation-type: tm+mt
source-git-commit: fbfea06bc2a4493b6d9b84a8f367749e1d803650

---


# 內容安全性原則及 Experience Cloud Identity 服務{#content-security-policies-and-the-experience-cloud-id-service}

內容安全性原則 (CSP) 是一項 HTTP 標題和安全性功能，能讓瀏覽器控制要在網頁中載入的資源類型。如果您使用 ID 服務，且訂下嚴格的 CSP 以使用白名單來接受來自值得信賴網域的資料，請檢視本節的內容。您需要將此處所列的 Adobe 網域新增至您的 CSP 白名單中。

## CSP 檢視 {#section-5fde5c00a678455c914b8307a8caab82}

CSP 會利用 HTTP 標頭 `Content-Security-Policy` 來控制瀏覽器要接受或在網頁中要載入的資源類型。套用 CSP 能協助您避免以下情形:

* 在來源為未知或未加入白名單的情況下載入 JavaScript 檔案。
* 遭受跨網站指令檔 (XXS) 的攻擊。
* 遭受資料插入攻擊。
* 遭受網站竄改攻擊。
* 惡意程式碼散播。

運用 CSP 是常見的作法，而且受到廣泛認同。本文件的目的並不在於詳細解釋 CSP (請參閱下方相關資訊的連結以取得更多資訊)。重要的是，您瞭解在使用 CSP 時應加上哪些 Adobe 網域名稱，以及訂下嚴謹的安全性原則。新增這些網域可讓存取您網站的訪客瀏覽器對您使用的 Experience Cloud 資源執行重要呼叫。

## 加入白名單的 Experience Cloud 網域 {#section-30693e9a96834edfbf04de9e698cf2aa}

將這些網域名稱或 URL 新增到每個使用的 Experience Cloud 解決方案或服務清單的 CSP 中。

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
   <td colname="col2"> <p>修改您的 CSP 以包含以下項目: </p> <p> 
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
   <td colname="col1"> <p> <b>訪客 ID 服務</b> </p> </td> 
   <td colname="col2"> <p>修改您的 CSP 以包含 <span class="codeph">*.demdex.net</span>。 </p> <p>對 <span class="codeph">demdex.net</span> 網域發出的呼叫用於產生 <a href="../introduction/cookies.md" format="dita" scope="local">Cookie 與 Experience Cloud Identity 服務</a>及用於 ID 同步。亦請參閱<a href="https://marketing.adobe.com/resources/help/en_US/aam/demdex-calls.html" format="https" scope="external">瞭解向 Demdex 網域進行的呼叫</a>。 </p> </td> </tr> 
 <tr>
 <td colname="col1"> <p> <b>Activity map外掛程式</b> </p> </td> 
 <td colname="col2"> <p>修改您的CSP以包含*omniture.com </p></td> 
 </tr>
 </tbody> 
</table>

>[!MORELIKETHIS]
>
>* [內容安全性原則參考](https://content-security-policy.com/)
>* [MDN: 內容安全性原則](https://developer.mozilla.org/en-US/docs/Web/HTTP/CSP)
>* [Wikipedia: 內容安全性原則](https://en.wikipedia.org/wiki/Content_Security_Policy)

