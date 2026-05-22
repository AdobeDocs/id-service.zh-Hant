---
description: 內容安全性原則 (CSP) 是 HTTP 標題和安全性功能，可讓瀏覽器控制要在網頁上載入的資源類型。 如果您使用ID服務，且具備使用允許清單接受來自受信任網域之資源的嚴格CSP，請檢閱此區段。 您需要將此處所列的Adobe網域新增至CSP允許清單。
keywords: ID 服務
title: 內容安全性原則及 Experience Cloud 身分識別服務
exl-id: e35c6809-764e-4c3e-9139-88bb92e82338
TQID: https://experienceleague.adobe.com/UX0RWE7v912XEHJCJE49yt1sy13t1P0I0I79gG9Z7m8
product_v2:
  - id: e1971122-7081-4556-9222-8a31bd71800c
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: f8a45b24-4be7-4f1b-909b-60d06b483a20
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2:
  - id: c2be0313-b3ae-45e0-b454-d20bf54b23f2
  - id: d095671a-1355-40aa-8b5f-06c33c68080b
source-git-commit: 5c41e39a833b527a329f62e5f0929445f47139de
workflow-type: tm+mt
source-wordcount: 530
ht-degree: 64%

---

# 內容安全性原則及 Experience Cloud 身分識別服務 {#content-security-policies-and-the-experience-cloud-id-service}

內容安全性原則 (CSP) 是 HTTP 標題和安全性功能，可讓瀏覽器控制要在網頁上載入的資源類型。 如果您使用ID服務，且具備使用允許清單接受來自受信任網域之資源的嚴格CSP，請檢閱此區段。 您需要將此處所列的Adobe網域新增至CSP允許清單。

## CSP 檢視 {#section-5fde5c00a678455c914b8307a8caab82}

CSP 會利用 HTTP 標頭 `Content-Security-Policy` 來控制瀏覽器要接受或在網頁中要載入的資源類型。 套用 CSP 能協助您避免以下情形：

* 如果來源不明或未包含在允許清單中，則不會載入JavaScript檔案。
* 跨網站指令碼 (XXS) 攻擊。
* 資料插入攻擊。
* 網站損毀攻擊。
* 惡意軟體散發。

CSP 的使用十分常見，且眾所周知。 本文件的目的並非詳細說明 CSP (如需詳細資訊，請參閱下方連結中的相關資訊)。 重要的是，您必須了解您在使用時應將何種 Adobe 網域名稱新增至 CSP，並擬定嚴格的安全性原則。 新增這些網域，可讓存取您的網站的訪客瀏覽器能夠對您使用的 Experience Cloud 資源進行重要呼叫。

## 加入允許清單的Experience Cloud網域 {#section-30693e9a96834edfbf04de9e698cf2aa}

針對您所使用的每個 Experience Cloud 解決方案或服務，請將下列網域名稱或 URL 新增至您的 CSP。

<table id="table_EC9FC999A62D4B7A830CE73B0AB9EF3C">
 <thead>
  <tr>
   <th colname="col1" class="entry">Experience Cloud 解決方案或服務</th>
   <th colname="col2" class="entry">說明</th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <td colname="col1">
    <p><b>AppMeasurement</b></p>
   </td>
   <td colname="col2">
    <p>修改您的 CSP 以包含以下項目：</p>
    <ul id="ul_7522AE83A03A4115A84DF5B32D6DD79B">
     <li id="li_AB1EC161FB154BEDA1BEFE76C8A38A90"><span class="codeph">*.2o7.net</span></li>
     <li id="li_4B12A283716746949201528CD6AF529E"><span class="codeph">*.omtrdc.net</span></li>
    </ul>
   </td>
  </tr>
  <tr>
   <td colname="col1">
    <p><b>Target</b></p>
   </td>
   <td colname="col2">
    <p>修改您的CSP以包含<span class="codeph">*.tt.omtrdc.net</span>。</p>
   </td>
  </tr>
  <tr>
   <td colname="col1">
    <p><b>Experience Cloud ID服務與Audience Manager</b></p>
   </td>
   <td colname="col2">
    <p>修改 CSP 以納入以下網域。</p>
    <ul>
     <li>connect-src 'self' <code>https://*.demdex.net https://cm.everesttech.net https://assets.adobedtm.com;</code></li>
     <li>img-src 'self' <code>https://*.demdex.net https://cm.everesttech.net https://assets.adobedtm.com;</code></li>
     <li>script-src 'self' <code>https://*.demdex.net https://cm.everesttech.net https://assets.adobedtm.com;</code></li>
     <li>frame-src 'self' <code>https://*.demdex.net;</code></li>
     <li>如果您是使用 Adobe Launch 部署標籤，也請將 <code>https://assets.adobedtm.com</code> 新增至網域清單。</li>
    </ul>
    <p>對<span class="codeph">demdex.net</span>網域發出的呼叫用於產生<a href="../introduction/cookies.md" format="dita" scope="local">Cookie與Experience Cloud Identity服務</a>及用於ID同步。 另請參閱<a href="https://experienceleague.adobe.com/docs/audience-manager/user-guide/reference/demdex-calls.html?lang=zh-Hant" format="https" scope="external">瞭解向Demdex網域進行的呼叫</a>。</p>
   </td>
  </tr>
  <tr>
   <td colname="col1">
    <p><b>Activity Map外掛程式</b></p>
   </td>
   <td colname="col2">
    <p>修改您的 CSP 以包含 *.adobe.com。 **注意**：如果您在 2020 年 1 日前即已安裝 Activity Map，您的瀏覽器仍會收到 *.omniture.com 的原始請求，但會將其重新導向 *.adobe.com。</p>
   </td>
  </tr>
  <tr>
   <td colname="col1">
    <p><b>Advertising Analytics</b></p>
   </td>
   <td colname="col2">
    <p>如果您限制查詢字串引數，則允許列出以下引數：</p>
    <ul>
     <li><code>s_kwcid</code> （使用<code>!</code>）</li>
     <li><code>ef_id</code> （使用<code>:</code>）</li>
    </ul>
    <p>如果您在URL中封鎖<code>!</code>字元，則也將其列入允許清單。</p>
    <p>Advertising Analytics僅使用<code>s_kwcid</code>，但Advertising Search、Social和Commerce以及Advertising DSP也使用<code>ef_id</code>。</p>
   </td>
  </tr>
  <tr>
   <td colname="col1">
    <p><b>Adobe Advertising</b></p>
   </td>
   <td colname="col2">
    <p>修改您的CSP以包含以下網域：</p>
    <ul>
     <li><code>.everestjs.net</code></li>
     <li><code>.everesttech.net</code></li>
    </ul>
   </td>
  </tr>
 </tbody>
</table>

>[!MORELIKETHIS]
>
>* [內容安全性原則參考](https://content-security-policy.com/)
>* [MDN：內容安全性原則](https://developer.mozilla.org/zh-TW/docs/Web/HTTP/CSP)
>* [Wikipedia：內容安全性原則](https://en.wikipedia.org/wiki/Content_Security_Policy)

