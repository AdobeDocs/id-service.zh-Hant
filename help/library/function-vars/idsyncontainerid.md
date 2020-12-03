---
description: 此屬性會設定資料來源容器 ID 以供 ID 同步之用。
keywords: ID Service
seo-description: 此屬性會設定資料來源容器 ID 以供 ID 同步之用。
seo-title: idSyncContainerID
title: idSyncContainerID
uuid: e35dc48b-1aa1-41e3-91c1-ef1e9d2d8b90
translation-type: tm+mt
source-git-commit: f7f23d89649a888f5e9d8c94526b550fbda7045b
workflow-type: tm+mt
source-wordcount: '334'
ht-degree: 58%

---


# idSyncContainerID{#idsynccontainerid}

此屬性會設定資料來源容器 ID 以供 ID 同步之用。

內容:

<ul class="simplelist"> 
 <li> <a href="../../library/function-vars/idsyncontainerid.md#section-b0c50732b1c84bed8616e82e8e83d58c" format="dita" scope="local"> 語法與程式碼範例 </a> </li> 
 <li> <a href="../../library/function-vars/idsyncontainerid.md#section-6aed44fbe9d6401a8f912cb0d98339a7" format="dita" scope="local"> 什麼是容器? 我會在何時使用到? </a> </li> 
 <li> <a href="../../library/function-vars/idsyncontainerid.md#section-f283cb69c8de4348b5316cc4e02a3e9e" format="dita" scope="local"> 在您使用 DIL 和 VisitorAPI.js 時設定容器 ID </a> </li> 
</ul>

## 語法與程式碼範例 {#section-b0c50732b1c84bed8616e82e8e83d58c}

**語法:** ` idSyncContainerID: *`容器 ID 值`*`

**程式碼範例:**

```js
var visitor = Visitor.getInstance ("Insert Experience Cloud organization ID here",{ 
   ... 
   //Set container ID 
   idSyncContainerID:80 
});
```

## 什麼是容器? 我會在何時使用到?    {#section-6aed44fbe9d6401a8f912cb0d98339a7}

**容器**

容器是 [!DNL Audience Manager] 建立的物件。雖然這些容器無法從外部存取，但這些容器會列出所有資料來源：

* 可供您使用，但未用於ID同步。
* 正用於ID同步。

即使您並非 [!DNL Audience Manager] 客戶，如果您在自己的網域中的不同網頁中，以各種資料來源來交換 ID，您的帳戶也會具有這些容器。這是因為 [!DNL Audience Manager] 提供的技術和後端功能允許進行 ID 同步。

**使用案例**

視您的情況而定，您可能需要或不需要將此組態新增至ID服務程式碼。

<table id="table_48621F343C7F4760A75F6BCC2DB2DA20"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> 條件 </th> 
   <th colname="col2" class="entry"> 說明 </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <b>不需要</b> </p> </td> 
   <td colname="col2"> <p>在下列情況下，您不需要使用此配置： </p> <p> 
     <ul id="ul_4D6F794CD65C43D0BEFBA6F5DE420C2E"> 
      <li id="li_0F048A6AC7BE4450AFA1B20B1AC25808">您透過任何 <span class="keyword">Experience Cloud</span> 解決方案使用 ID 服務，且沒有透過其他資料來源執行 ID 同步。在此情況下，您的帳戶會有ID為0的預設容器，而不需執行任何動作。 </li> 
      <li id="li_5657D64D9406407D9B4DB7D8BE4F8EE4">您的所有資料來源都位於單一容器中。 </li> 
     </ul> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>需要</b> </p> </td> 
   <td colname="col2"> <p>當所有這些條件都適用時，您需要使用此組態： </p> <p> 
     <ul id="ul_9AFD14FC5A2745F7BD7BE7B64545DA62"> 
      <li id="li_04F0EFBBD71B43608CAAA7E7409D33FE">您沒有使用 <span class="keyword">Audience Manager</span>。 </li> 
      <li id="li_4BFA6DC76CE9455EBBC337FD2FE820BF">您需要將ID與依容器組織的其他資料來源同步。 </li> 
      <li id="li_731DA5D1CBF244F8BEBE57C0E2EBA713">您需要將ID與網域不同頁面上不同容器中的資料來源同步。 </li> 
     </ul> </p> </td> 
  </tr> 
 </tbody> 
</table>

## 在您使用 DIL 和 VisitorAPI.js 時設定容器 ID {#section-f283cb69c8de4348b5316cc4e02a3e9e}

If you have deployed [!UICONTROL DIL ]*and* VisitorAPI.js on the same page:

* 若為 ID 同步，則訪客 ID 服務程式碼會的優先順序會高於 DIL。
* 僅在 ID 服務程式碼中設定 `idSyncContainerID`。

