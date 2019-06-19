---
description: 選用的布林值設定，可決定 ID 服務是否要將資料傳送至 Adobe Experience Cloud Device Co-op。
keywords: ID 服務
seo-description: 選用的布林值設定，可決定 ID 服務是否要將資料傳送至 Adobe Experience Cloud Device Co-op。
seo-title: isCoopSafe
title: isCoopSafe
uuid: 4dfa1f35-0a88-48d1-9484-d88 cb53 ad461
translation-type: tm+mt
source-git-commit: bc5c81455023e22e64877bb861dfe141e158599c

---


# isCoopSafe{#iscoopsafe}

選用的布林值設定，可決定 ID 服務是否要將資料傳送至 Adobe Experience Cloud Device Co-op。

內容:

<ul class="simplelist"> 
 <li> <a href="../../library/function-vars/coopsafe.md#section-4883eda6beb8437182bcc82bb58fae41" format="dita" scope="local"> 需求 </a> </li> 
 <li> <a href="../../library/function-vars/coopsafe.md#section-d18af2b903f248e18ae8108aaf0a8ebb" format="dita" scope="local"> 使用個案 </a> </li> 
 <li> <a href="../../library/function-vars/coopsafe.md#section-952f56724a2b4d349340e26fbaf33ddd" format="dita" scope="local"> 語法與程式碼範例 </a> </li> 
 <li> <a href="../../library/function-vars/coopsafe.md#section-fcd441933506493faefaa6b51f194a17" format="dita" scope="local"> 事件呼叫 POST 參數 </a> </li> 
 <li> <a href="../../library/function-vars/coopsafe.md#section-9281c39c8b6249d7864100b5cbca7dc6" format="dita" scope="local"> Post-Instantiation API </a> </li> 
</ul>

## 要求 {#section-4883eda6beb8437182bcc82bb58fae41}

若要使用 `isCoopSafe` ，您必須：

* 使用 2.4 版或更新版本的 ID 服務程式碼。
* 參與 [Experience Cloud Device Co-op](https://marketing.adobe.com/resources/help/en_US/mcdc/)。潛在的 Co-op 成員也需審閱此文件，以確定 `isCoopSafe` 是否解決了關於如何使用資料建立裝置圖形的可能問題。

* 請和您的 [!DNL Adobe] 顧問合作，在您的 Device co-op 帳戶上設定白名單或是黑名單標幟。沒有啟用可這些標幟的自助式路徑。

## 使用個案 {#section-d18af2b903f248e18ae8108aaf0a8ebb}

`isCoopSafe` 有助於解決關於 Device co-op 現有或潛在成員資料收集的 2 個使用案例。這些關於網站訪客資料如何傳給 Device co-op 的使用案例有助於建立設備圖形。以下表格說明 `isCoopSafe` 如何搭配其他使用案例以封鎖或傳送資料給裝置圖形

<table id="table_A24C63D2A21F47EDBAC8FA5E7BE888D8"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> 使用案例 </th> 
   <th colname="col2" class="entry"> 說明 </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <b>已驗證的訪客</b> </p> </td> 
   <td colname="col2"> <p>新增 <span class="codeph">isCoopSafe</span> 至您的 ID 服務程式碼，以控制 Device Co-op 該如何使用已驗證且接受或是未接受使用條款的訪客資料來建立裝置圖形。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>第三方網站上的 DIL</b> </p> </td> 
   <td colname="col2"> <p>新增 <span class="codeph">isCoopSafe</span> 至您的 ID 服務程式碼，以便在第三方網站上使用；因此，您可能會: </p> <p> 
     <ul id="ul_C27BB26510314834A2A7CD99D46DA4AC"> 
      <li id="li_4E6AE574F18646F09C0CF4553EEA1A9E">無法確保已驗證的訪客是否已經接受使用者條款。 </li> 
      <li id="li_26D0561BF32B4278B0A6B5082C17FED8">需要控制 Device Co-op 使用資料的方式，以建立裝置圖形。 </li> 
     </ul> </p> </td> 
  </tr> 
 </tbody> 
</table>

## 語法與程式碼範例 {#section-952f56724a2b4d349340e26fbaf33ddd}

**語法:** `isCoopSafe: true | false`

布林值選項決定 Device Co-op 是否使用客戶資料。

* `isCoopSafe: true`: 行動 SDK 或是網站所蒐集的訪客資料*可以*用來協助建立裝置圖形。

* `isCoopSafe: false`: 行動 SDK 或是網站所蒐集的訪客資料*不可以*用來協助建立裝置圖形。

**程式碼範例**

當您的 ID 服務程式碼實例化時，設定此項:

```js
var visitor = Visitor.getInstance("Insert Experience Cloud organization ID here",{ 
     ... 
     isCoopSafe: true 
});
```

## 事件呼叫 POST 參數 {#section-fcd441933506493faefaa6b51f194a17}

取決於您設定的標幟 (`true` 或 `false`)，ID 服務將 `isCoopSafe` 轉譯為 POST 參數並在事件呼叫時將參數傳送至 [!DNL Adobe]:

* `d_coop_safe=1`
* `d_coop_unsafe=1`

POST 參數告知 [!DNL Experience Cloud] Device Co-op 是否能在裝置圖像中包含使用者資料。以下表格定義了在事件呼叫中 `isCoopSafe` 布林值標幟與所傳遞的 POST 參數之間的關係。如果您沒有使用 `isCoopSafe`，這些都不會在事件呼叫中傳遞。

<table id="table_0A544534CA904F4D9836A34B8C1EACBB"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> 設定狀態 </th> 
   <th colname="col2" class="entry"> POST 參數 </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> isCoopSafe: true </span> </p> </td> 
   <td colname="col2"> <p> <span class="codeph"> d_coop_safe=1 </span> </p> <p>Device Co-op 可以使用訪客資料來協助建立裝置圖像。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> isCoopSafe: false </span> </p> </td> 
   <td colname="col2"> <p> <span class="codeph"> d_coop_unsafe=1 </span> </p> <p>Device Co-op 不可以使用訪客資料來協助建立裝置圖像。 </p> </td> 
  </tr> 
 </tbody> 
</table>

## Post-Instantiation API {#section-9281c39c8b6249d7864100b5cbca7dc6}

這些 API 允許您覆寫 `isCoopSafe` 狀態。這些都是必要措施，因為它們可以讓您在網站或未重新整理的單頁應用程式中變更訪客實例化之後/登錄之後的狀態。舉例來說，如果用戶向您的網站或應用程式進行身份驗證，並隨後接受使用者條款原則允許 Device Co-op 使用其資料，則您可能需要呼叫這些 API。

<table id="table_BAA96B1F82BE48C3A61A1AF1367BA45C"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> API </th> 
   <th colname="col2" class="entry"> 說明 </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> visitor.setAsCoopSafe(); </span> </p> </td> 
   <td colname="col2"> <p>在後續事件呼叫中，設定 POST 參數 <span class="codeph">d_coop_safe=1</span>。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> visitor.setAsCoopUnsafe(); </span> </p> </td> 
   <td colname="col2"> <p>在後續事件呼叫中，設定 POST 參數 <span class="codeph">d_coop_unsafe=1</span>。 </p> </td> 
  </tr> 
 </tbody> 
</table>

<!--
Wiki page https://wiki.corp.adobe.com/x/RCfFTg
-->

>[!MORE_贊_ this]
>
>* [DIL isCoopSafe](https://marketing.adobe.com/resources/help/en_US/aam/dil-coopsafe.html)

