---
description: 2017年訪客ID服務的功能發佈、更新或變更。
keywords: 訪客 ID 服務
title: 2017 年版本注意事項
exl-id: 0b51d3b1-e405-4473-9e1a-f89a55250e5e
TQID: https://experienceleague.adobe.com/lt0zISb6FrqIuziYTt8pA6VZyU4XQkVsIha19v-LU7w
product_v2: id: e1971122-7081-4556-9222-8a31bd71800c
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554id: c66ffd68-0f65-42bb-aa23-b4020f12e0bdid: f8a45b24-4be7-4f1b-909b-60d06b483a20id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2: id: a004cc84-67b9-4a33-a3a7-8ec7273ef4dcid: c2be0313-b3ae-45e0-b454-d20bf54b23f2id: d095671a-1355-40aa-8b5f-06c33c68080bid: d3cdead0-685a-4489-9250-4bb709942f66
source-git-commit: 09ee359440c122702a6ce83708c98af3862c9cc9
workflow-type: tm+mt
source-wordcount: 751
ht-degree: 47%

---

# 2017 年版本注意事項 {#release-notes}

2017年訪客ID服務的功能發佈、更新或變更。

這些變更也包含在[CX Enterprise發行說明](https://experienceleague.adobe.com/docs/release-notes/experience-cloud/current.html?lang=zh-Hant)中。

>[!NOTE]
>
>2017 年 3 月、4 月、5 月和 10 月均沒有針對客戶提供的版本注意事項或程式碼變更。 對於上述月份，訪客ID服務程式碼均維持v2.1版不變。

## 2.5 版 {#section-27b441509124493f80984ed09bd9e88b}

2017 年 9 月

<!--
<p>
<note type="important">
Visitor ID Service support for Internet Explorer 6, 7, and 8 is deprecated and will be discontinued in a future release.
</note> </p>
-->

<table id="table_FD24C06C7B3547C3A7673C46B1852A35"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> 功能 </th> 
   <th colname="col2" class="entry"> 說明 </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> getVisitorValues</span> </p> </td> 
   <td colname="col2"> <p>這是非同步API，依預設會為Analytics、訪客ID服務、資料收集退出、地理位置以及中繼資料「blob」內容傳回識別碼。 您也可以透過選擇性的 <span class="codeph">visitor.FIELDS</span> 列舉控制您要傳回的 ID。 請參閱 <a href="../library/get-set/getvisitorvalues.md#reference-b8c9e17c170c4291829a792df46ce279" format="dita" scope="local">getVisitorValues</a>。 </p> </td> 
  </tr> 
 </tbody> 
</table>

**錯誤修正與其他變更**

* 已修正Chrome相關錯誤，該錯誤導致訪客ID服務在按一下瀏覽器中的上一頁按鈕時擲回錯誤。
* 現在，當事件呼叫回應中的地區ID變更時，訪客ID服務會重新引發ID同步。
* 新增了新的檔案[內容安全性原則及訪客ID服務](/help/reference/csp.md#concept-968c423a7392479db0a0d821ae9783e3)，說明如何將訪客ID服務使用的Adobe網域呼叫加入白名單。

<!--
## Version 2.4 {#section-f4d1608dd8894f558a92b82e83321200}

August, 2017

<table id="table_D9623D34F4444B038F7835750932C8AA"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Feature </th> 
   <th colname="col2" class="entry"> Description </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> isCoopSafe</span> </p> </td> 
   <td colname="col2"> <p>An optional, Boolean configuration that determines if the Visitor ID Service sends (or does not send) data to the Adobe Device Co-op. See <a href="../library/function-vars/coopsafe.md#reference-7fbed36f38a048d1a5883c53d430ddf4" format="dita" scope="local"> isCoopSafe</a>. </p> </td> 
  </tr> 
 </tbody> 
</table>

**Revised Documentation**

Updated and revised the [FAQs](/help/faq-intro/faq-intro.md) to include separate FAQs for different CX Enterprise solutions. 
-->

## 2.3 版 {#section-ae7b1cb1e52e4ca5a46b453a3ba1f571}

2017 年 7 月

<table id="table_1448040D09B94A74883A694FCF91EB33"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> 功能 </th> 
   <th colname="col2" class="entry"> 說明 </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> sdidParamExpiry</span> </p> </td> 
   <td colname="col2"> <p>將其新增至 <span class="codeph">Visitor.getInstance</span> 函式後，此設定可讓您從某一頁面傳遞 Supplemental Data ID (SDID) 至另外一個頁面時，覆寫該 ID 的預設過期時間間隔。 您可以使用 <span class="codeph">sdidParamExpiry</span> 搭配 <span class="codeph">appendSupplimentalDataTo</span> Helper 函式。 請參閱 <a href="../library/function-vars/sdidparamexpiry.md#reference-cef3fd03c43b4772b2422e220b40a458" format="dita" scope="local">sdidParamExpiry</a>。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> resetState</span> </p> </td> 
   <td colname="col2"> <p>此功能主要是為 A4T 客戶所設計，可協助解決在單一網站/螢幕或應用程式處理 ID 時遇到的問題。 請參閱 <a href="../library/get-set/resetstate.md#reference-47fc00ae139042d795d78244d9970139" format="dita" scope="local">resetState</a>。 </p> </td> 
  </tr> 
 </tbody> 
</table>

**錯誤修正與其他變更**

* 修正`VisitorAPI.js` v2.2中造成訪客ID服務與Target無法在Internet Explorer中搭配運作的錯誤。
* 修訂程式碼，協助改善訪客ID服務將資料傳送至Destination Publishing iFrame的方式。 這有助於降低 CPU 使用量。

## 2.2 版 {#section-b7dee2495c29470e9b3a3132ec1fd951}

發行日期：2017 年 6 月

<table id="table_7E412383E89D46759B00FE7328C9946F"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> 功能 </th> 
   <th colname="col2" class="entry"> 說明 </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <a href="../library/function-vars/whitelistdomain.md#reference-999899ff7b5b429a8824c9db7a379808" format="dita" scope="local"> whitelistParentDomain 及 whitelistIframeDomains </a> </p> </td> 
   <td colname="col2"> <p>這些設定可讓實作於iFrame和上層頁面的不同訪客ID服務程式碼例項互相通訊。 這些設定可在您不一定控制上層頁面/網域，且在您已控制之網域的iFrame中載入訪客ID服務程式碼的情況下，協助解決2個特定使用案例的問題。 </p> </td> 
  </tr> 
 </tbody> 
</table>

## 5 月的文件更新 {#section-1d36b91bb7a140ce8a145251ffac9f2f}

<table id="table_CD031A716A694E8FA89695C9B614BC91"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> 主題 </th> 
   <th colname="col2" class="entry"> 說明 </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <a href="../faq-intro/faq.md" format="dita" scope="local"> 常見問題集 </a> </p> </td> 
   <td colname="col2"> <p>更新 <span class="keyword">Analytics</span> 一節，提供如何尋找追蹤伺服器資訊的相關資訊。 </p> </td> 
  </tr> 
 </tbody> 
</table>

## 4 月的文件更新 {#section-df3e5a85448c4001a6791517520ae06e}

<table id="table_ADC2636240654C69B8B6A45849024540"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> 主題 </th> 
   <th colname="col2" class="entry"> 說明 </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <a href="../library/function-vars/subdomain-config.md#reference-8ad017b3e5d24d34b3da25e8f8a56196" format="dita" scope="local"> audienceManagerServer 及 audienceManagerServerSecure </a> </p> </td> 
   <td colname="col2"> <p>新增 <span class="keyword">Audience Manager</span> 文件的連結以說明對 <span class="codeph">demdex.net</span> 網域進行的呼叫。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <a href="../library/function-vars/subdomain-config.md" format="dita" scope="local"> 了解 ID 同步和匹配率 </a> </p> </td> 
   <td colname="col2"> <p>修訂 <span class="keyword">Media Optimizer</span> 章節以說明對 <span class="codeph">cm.eversttech.net</span> 的呼叫。 這是訪客ID服務透過<span class="keyword"> Media Optimizer</span>執行的自動ID同步。 此功能已於 2017 年 1 月推出。 請參閱下方的 <a href="../release-notes/notes-2017.md#section-0ceac6007c1241b58ad607e2b76b2b7e" format="dita" scope="local">2.0 版</a>。 </p> </td> 
  </tr> 
 </tbody> 
</table>

## 2.1 版 {#section-5e666dc47c2f4f92999e92697d75799e}

發行日期：2017 年 2 月

**功能**

<table id="table_1F7E1CF091604D22B1D9F3F1AE4DB2D7"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> 功能 </th> 
   <th colname="col2" class="entry"> 說明 </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> 訪客ID服務API屬性，<span class="codeph"> idSyncContainerID</span></p> </td> 
   <td colname="col2"> <p>該屬性會設定 <span class="keyword">Audience Manager</span> 所使用的容器 ID 以供 ID 同步之用。 請參閱 <a href="/help/library/function-vars/idsyncontainerid.md" format="https" scope="external">idSyncContainerID</a>。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>訪客ID服務API方法，<span class="codeph">appendSupplementalDataIDTo(<span class="varname"> URL</span>，<span class="varname"> SDID</span>)</span></p> </td> 
   <td colname="col2"> <p>此公用方法可附加至 <span class="wintitle">Supplemental Data ID</span> (SDID) 作為查詢字串參數，以重新導向 URL。 請參閱 <a href="../library/get-set/appendsupplementaldataidto.md#reference-65d09de6fde0418f8c62fa79304a755d" format="dita" scope="local"> appendSupplementalDataIDTo</a>。 (MCID-285) </p> </td> 
  </tr> 
 </tbody> 
</table>

**修正**

修正訪客ID服務會針對ID重複發出伺服器呼叫，而不使用AMCV Cookie中儲存之ID的錯誤。 (MCID-296)

**新增文件**

[搭配不同的CX企業解決方案和服務使用DNS預先擷取](https://experienceleague.adobe.com/docs/core-services/interface/more-resources/dns-prefetch.html?lang=zh-Hant)

## 2.0 版 {#section-0ceac6007c1241b58ad607e2b76b2b7e}

2017 年 1 月

>[!IMPORTANT]
>
>訪客ID服務程式碼v2.0依預設會自動與Adobe Media Optimizer同步ID。 這表示您會看到從頁面對`cm.eversttech.net`的呼叫，這是由Adobe控制的舊版Media Optimizer網域。 另請參閱[了解 ID 同步和比對率](../introduction/match-rates.md#concept-e55cf228b90c457fbee8c3cb06b195ab)。

**修正和改良**

* 已修正致使 AppMeasurement 無法對 Analytics 進行追蹤呼叫的錯誤。 (MCID-254、MCID-256、MCID-286)
* 修正當訪客啟用廣告封鎖程式而該封鎖程式被設定為排除demdex.net網域時，訪客ID服務無法立即失效的錯誤。 這是相當罕見且不尋常的錯誤，因為大多數的廣告封鎖工具並不會封鎖 demdex.net 網域。 (MCID-233)
* 修正訪客ID服務程式碼與客戶網站上的自訂指令碼之間的互動所造成的錯誤。 此問題導致 Internet Explorer 9 無法載入網頁。 (MCID-206)

## 過去幾年 {#section-aaabe2b7b0f04641b24acffc11cd7d2e}

舊版訪客ID服務發行說明。

