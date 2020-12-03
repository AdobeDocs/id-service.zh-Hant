---
description: 這些範例涵蓋與直接整合和Experience Cloud ID(MID)相關的2個常見使用案例。 MID是網站訪客的唯一、永續性ID。
keywords: ID Service
seo-description: 這些範例涵蓋與直接整合和Experience Cloud ID(MID)相關的2個常見使用案例。 MID是網站訪客的唯一、永續性ID。
seo-title: 直接整合的使用案例
title: 直接整合的使用案例
uuid: 6de1eb8b-4783-4545-8a64-ab6b9ef93432
translation-type: tm+mt
source-git-commit: ec67177fc6491e4c8cea835d198574c9fdb4b01f
workflow-type: tm+mt
source-wordcount: '473'
ht-degree: 48%

---


# 直接整合的使用案例 {#direct-integration-use-cases}

這些範例涵蓋 2 個與直接整合和 Experience Cloud ID (ECID 或 MID) 相關的常見使用案例。此 ID 是每個網站訪客專屬的永久性唯一 ID。

>[!TIP]
>
>* 參閱使用案例前，請先檢閱並瞭解[程式碼語法和變數](../implementation-guides/direct-integration.md#concept-4cd3206a84bb4687af0b312ae09648b9)。
>* 如需有關 MID 的詳細資訊，請參閱 [Cookie 與 Experience Cloud Identity 服務](../introduction/cookies.md)。

>



## 使用案例 1：我有 Experience Cloud ID (MID)，但想傳遞我自己的訪客 ID，並設定驗證狀態 {#section-a67d89a343754d1286d03cf08d34b806}

<table id="table_DA8840FCB51541109FE6DF20430E8924"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> 使用案例元素 </th> 
   <th colname="col2" class="entry"> 說明 </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <b>條件</b> </p> </td> 
   <td colname="col2"> <p>此使用案例假設您： </p> 
    <ul id="ul_F20231F83EE84889B78971A64E758757"> 
     <li id="li_20F3E96493724CD2BAF4B20AEE5CBF23">請為網站訪客設定MID。 我們稱之為ID 1234。 </li> 
     <li id="li_A358C58CC58C4FCBB7250F5ED108AA71">依您自己的唯一ID瞭解此訪客。 我們打這個9876號。 </li> 
     <li id="li_D93CE7182EBE4927A5C7A0BF414C03BC">想要將MID(1234)連結至您自己的唯一ID(9876)。 </li> 
     <li id="li_4611146E56624C2AB647733487A3F046"> <i>（可選）</i> ，想要設定此訪客的驗證狀態。 </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>動作</b> </p> </td> 
   <td colname="col2"> <p>基於上述條件，請對 ID 服務進行呼叫，並須包含： </p> 
    <ul id="ul_9ECB1A65266644E89E949C57D202D5A4"> 
     <li id="li_10A6F5A9C54D44A08F4F2E405E6019E2">MID(1234)。 </li> 
     <li id="li_4869572B40E54C54B88A2474DAC475A8">您的資料提供者ID。 這是指派給您公司的唯一ID。 我們稱之為4444。 </li> 
     <li id="li_05C8ED47488C4E289D84093127EC7B19">您的訪客ID(9876)。 </li> 
     <li id="li_3D1556AD18C843828A362CC604A9F76B"> <i>（選用）</i> ，用於定義此訪客之驗證狀態的狀態ID。 </li> 
    </ul> <p>此外，如果您碰巧有直接整合指南中列出的任何其 <a href="../implementation-guides/direct-integration.md#concept-4cd3206a84bb4687af0b312ae09648b9" format="dita" scope="local"> 他參數</a> (例如<span class="codeph"> d_blob</span> 或 <span class="codeph"> dcs_region</span>，等等) 也可以把它們傳進來。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>解決方案與程式碼範例</b> </p> </td> 
   <td colname="col2"> <p>呼叫 ID 服務的格式如下所示： </p> <p> <span class="codeph">https://dpm.demdex.net/id?d_mid=1234&amp;d_cid=4444%019876%011&amp;d_ver=2</span> </p> <p>請注意，範例呼叫包含以下內容的方式： </p> 
    <ul id="ul_0667FBFD8D3C46BDBD027F484691EC97"> 
     <li id="li_FAB1FAE703DB48D1A32EE72684028964">MID：<span class="codeph">d_mid=1234</span> </li> 
     <li id="li_C97B74FF444F4BB4B4A5CB1CBBE52249">加入您的訪客唯一 ID 的 MID：<span class="codeph">d_mid=1234&amp;d_cid=4444%019876%011</span> </li> 
     <li id="li_D428DBF765234DD78DDF152C5EE8AB69">驗證狀態 ID：<span class="codeph">...d_cid=4444%019876%011</span> (提示：這是最後一碼)。 </li> 
    </ul> </td> 
  </tr> 
 </tbody> 
</table>

## 使用案例 2：我沒有 MID 且需要產生一個 MID {#section-8e81291f8b684de8b88fae4002ae0029}

<table id="table_666A92693F8A413096DF6A64770C1141"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> 使用案例元素 </th> 
   <th colname="col2" class="entry"> 說明 </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <b>條件</b> </p> </td> 
   <td colname="col2"> <p>此使用案例假設您： </p> 
    <ul id="ul_BF3BD821907B46A4B2EFA63146D35722"> 
     <li id="li_E658AE0671D14558B65FDD8992F25996">網站訪客沒有MID。 </li> 
     <li id="li_28A48BB3F71C4E4297F95A2D3E10AD7B">需要向ID服務請求MID。 </li> 
     <li id="li_E2C306B9308D41E5BFE2F23EF48F5A41">知道您的<a href="../reference/requirements.md#section-a02f537129a64ffbb690d5738d360c26" format="dita" scope="local">組織 ID</a>。我們打這個5555 </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>動作</b> </p> </td> 
   <td colname="col2"> <p>有了這些條件，請呼叫包含您的組織ID的ID服務。 </p> <p>此外，如果您碰巧有直接整合指南中列出的任何其 <a href="../implementation-guides/direct-integration.md#concept-4cd3206a84bb4687af0b312ae09648b9" format="dita" scope="local"> 他參數</a> (例如<span class="codeph"> d_blob</span> 或 <span class="codeph"> dcs_region</span>，等等) 也可以把它們傳進來。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>解決方案與程式碼範例</b> </p> </td> 
   <td colname="col2"> <p>呼叫 ID 服務的格式如下所示： </p> <p> <span class="codeph">https://dpm.demdex.net/id?d_orgid=5555&amp;d_ver=2</span> </p> <p>請注意，範例呼叫含有您組織 ID <span class="codeph">(d_orgid=5555)</span> 的方式。系統會傳回此訪客的 <span class="keyword">Experience Cloud</span> ID。 </p> </td> 
  </tr> 
 </tbody> 
</table>

