---
description: 如果客戶的裝置無法接受或使用我們的 JavaScript 或 SDK 程式碼，本實作能讓他們在這些裝置上使用該 ID 服務，這類裝置包括遊戲主機、智慧型電視，或其他可上網的設備等等。請參閱本節，以取得語法、程式碼範例和定義。
keywords: ID 服務
title: 與 Experience Cloud Identity Service 直接整合
exl-id: 29565b74-5fe7-41f7-b278-6a90559faab9
source-git-commit: cb89ac70e37f35d5e4e2b971f2df9645304522f8
workflow-type: tm+mt
source-wordcount: '632'
ht-degree: 98%

---

# 與 Experience Cloud Identity Service 直接整合 {#direct-integration-with-the-experience-cloud-id-service}

如果客戶的裝置無法接受或使用我們的 JavaScript 或 SDK 程式碼，本實作能讓他們在這些裝置上使用該 ID 服務，這類裝置包括遊戲主機、智慧型電視，或其他可上網的設備等等。請參閱本節，以取得語法、程式碼範例和定義。

## 語法 {#section-a4754afec5ad40b6be00d6f1011d68bb}

如果裝置無法使用 VisitorAPI.js 或 SDK 程式碼程式庫，可以直接呼叫由 ID 服務使用的資料收集伺服器 (DCS)。若要這麼做，您可以呼叫 `dpm.demdex.net`，並根據下列格式提出要求。*斜體*&#x200B;表示變數預留位置。

![](assets/directSyntax.png)

在這個語法範例中，前置詞 `d_` 會做為系統層級變數，用於識別呼叫中的機碼-值組。您可以將幾個 `d_` 參數傳遞至 ID 服務，但要把重點放在上述程式碼中的機碼-值組上。如需其他變數的詳細資訊，請參閱[支援的 DCS API 呼叫屬性](https://experienceleague.adobe.com/docs/audience-manager/user-guide/api-and-sdk-code/dcs/dcs-api-reference/dcs-keys.html?lang=zh-Hant)。

ID 服務支援 HTTP 和 HTTPS 呼叫。使用 HTTPS 從安全頁面傳送資料。

## 範例要求 {#section-26302b8851704888b6f8e6b2071bcdb0}

您的請求可能會如下列範例所示。長變數已縮短。

![](assets/directExample.png)

## 範例回應 {#section-89bc103b3e9e4a8b98e74c32897b1200}

ID 服務會傳回 JSON 物件中的資料，如下所示。您的回應可能不同。

```js
{
     "d_mid":"12345",
     "dcs_region":"6",
     "id_sync_ttl":"604800",
     "d_blob":"wxyz5432"
}
```

## 已定義的要求與回應引數 {#section-4a9912b545364dc4acad4f1ea5ec641d}

**請求參數**

<table id="table_C8FFA89AB74E4E31A6926CDE5CD54217"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> 參數 </th> 
   <th colname="col2" class="entry"> 說明 </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> dpm.demdex.net</span> </p> </td> 
   <td colname="col2"> <p>由 <span class="keyword">Adobe</span> 控制的舊版網域。請參閱<a href="https://experienceleague.adobe.com/docs/audience-manager/user-guide/reference/demdex-calls.html?lang=zh-Hant" format="https" scope="external">了解向 Demdex 網域進行的呼叫</a>。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> d_mid</span> </p> </td> 
   <td colname="col2"> <p>Experience Cloud 訪客 ID。請參閱 <a href="../introduction/cookies.md" format="dita" scope="local">Cookie 與 Experience Cloud Identity Service</a>。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> d_orgid</span> </p> </td> 
   <td colname="col2"> <p>您的 Experience Cloud 組織 ID。如需尋找此 ID 的相關協助，請參閱 <a href="../reference/requirements.md" format="dita" scope="local">Experience Cloud Identity Service 的需求</a>。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> d_cid</span> </p> </td> 
   <td colname="col2"> <p>此選用參數會將資料提供者 ID (DPID)、唯一用戶 ID (DPUUID) 及<a href="../reference/authenticated-state.md" format="dita" scope="local">驗證狀態 ID</a> 傳給 ID 服務。如程式碼範例所示，以非列印用的控制字元 <span class="codeph">%01</span> 將 DPID 和 DPUUID 隔開。 </p> <p> <b>DPID 與 DPUUID</b> </p> <p>在 <span class="codeph">d_cid</span> 參數中，將每個相關的 DPID 和 DPUUID 組合指派至相同的 <span class="codeph">d_cid</span> 參數。如此，能讓您在單一要求中傳回多個 ID 集合。另外，以非列印用的控制字元 <span class="codeph">%01</span> 將 DPID、DPUUID 和選用的驗證標幟隔開。在下列範例中，提供者和用戶的 ID 都會以<b>粗體</b>文字強調顯示。 </p> 
    <ul id="ul_2E19D837296B40E9ACD096495CF711C5"> 
     <li id="li_5B94B057654440B99B989BA60E4ED053">語法：<span class="codeph">...d_cid=DPID%01DPUUID%01authentication state...</span> </li> 
     <li id="li_B07833EF51D54F088574B7B7F9FB841A">範例：<span class="codeph">...d_cid=123%01456%011...</span> </li> 
    </ul> <p> <b>驗證狀態</b> </p> <p>這是 <span class="codeph">d_cid</span> 參數中的選用 ID，以整數方式呈現，而且能根據下列用戶的驗證狀態來識別用戶: </p> 
    <ul id="ul_E2B36922B11C4AA2A9016B6E2DC9EDAA"> 
     <li id="li_31C018E3F9514B938C73EF40C436715F"> <span class="codeph"> 0</span> (未知) </li> 
     <li id="li_1F125C3879324C2F8EF4613C0ECB5F02"> <span class="codeph"> 1</span> (驗證) </li> 
     <li id="li_EF6792D0115D407485079D5D7480D965"> <span class="codeph"> 2</span> (登出) </li> 
    </ul> <p>若要指定驗證狀態，可在用戶 ID (UUID) 變數後方設定此標幟。以非列印用的控制字元 <span class="codeph">%01</span> 將 UUID 和選用的驗證標幟隔開。在下列範例中，驗證 ID 會以<b>粗體</b>文字強調顯示。 </p> <p>語法：<span class="codeph">...d_cid=DPID%01DPUUID%01authentication state</span> </p> <p>範例: </p> 
    <ul id="ul_4C1054CE860A4D9C8DD85C2A8020C47F"> 
     <li id="li_AD4000BF3E0146C0BD37B1EC513EC314">未知：<span class="codeph">...d_cid=123%01456%010...</span> </li> 
     <li id="li_B037D424AADA4D41BF29381A9602AE61">驗證：<span class="codeph">...d_cid=123%01456%011...</span> </li> 
     <li id="li_0410FCB9E60D4DD08E7898D814E1C3C9">登出：<span class="codeph">...d_cid=123%01456%012...</span> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> dcs_region</span> </p> </td> 
   <td colname="col2"> <p>ID 服務是分散於各處且負載平衡的系統。ID 可識別處理呼叫的資料中心所在的地區。請參閱 <a href="https://experienceleague.adobe.com/docs/audience-manager/user-guide/api-and-sdk-code/dcs/dcs-api-reference/dcs-regions.html?lang=zh-Hant" format="https" scope="external">DCS 地區 ID、位置與主機名稱</a>。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> d_cb</span> </p> </td> 
   <td colname="col2"> <p> <i>(選用)</i> 回呼參數可讓您執行要求內文中的 JavaScript 函數。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> d_blob</span> </p> </td> 
   <td colname="col2"> <p>JavaScript 中繼資料的加密區塊。大小限制將 blob 限制為 512 個位元組或更小。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> d_ver</span> </p> </td> 
   <td colname="col2"> <p>必填。此參數會設定 API 版本號碼。將此值設定為 <span class="codeph">d_ver=2</span>。 </p> </td> 
  </tr> 
 </tbody> 
</table>

**回應參數**

部分回應參數是請求的一部分，已定義於上一節中。

<table id="table_58D0E8876DDC4A81B1F24F845E87EC18"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> 參數 </th> 
   <th colname="col2" class="entry"> 說明 </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> id_sync_ttl</span> </p> </td> 
   <td colname="col2"> <p>重新同步間隔，以秒為單位指定。預設間隔為 604,800 秒 (7 天)。 </p> </td> 
  </tr> 
 </tbody> 
</table>
