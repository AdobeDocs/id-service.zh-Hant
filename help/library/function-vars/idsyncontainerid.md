---
description: 此屬性會設定資料來源容器 ID 以供 ID 同步之用。
keywords: 訪客 ID 服務
title: idSyncContainerID
exl-id: 6c4cd41b-902b-4872-8c3f-475a834b76f4
TQID: https://experienceleague.adobe.com/bDW5Z4LKbLW2igmRsJ-QxajnBj8KyvoTypUjUekElj4
product_v2:
  - id: e1971122-7081-4556-9222-8a31bd71800c
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: f8a45b24-4be7-4f1b-909b-60d06b483a20
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
source-git-commit: 09ee359440c122702a6ce83708c98af3862c9cc9
workflow-type: tm+mt
source-wordcount: 328
ht-degree: 60%

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

**語法：** `idSyncContainerID: *`容器 ID 值`*`

**程式碼範例:**

```js
var visitor = Visitor.getInstance ("INSERT-IMS-ORG-ID-HERE",{ 
   ... 
   //Set container ID 
   idSyncContainerID:80 
});
```

## 什麼是容器? 我會在何時使用到? {#section-6aed44fbe9d6401a8f912cb0d98339a7}

**容器**

容器是Audience Manager建立的物件。 雖然無法從外部存取這些容器，但是它們會列出所有具有以下特性的資料來源：

* 可供您使用但不是用於 ID 同步的資料來源。
* 正用於 ID 同步的資料來源。

即使您並非Audience Manager客戶，如果您在自己的網域中的不同頁面中，以各種資料來源來交換ID，您的帳戶也會具有這些容器。 這是因為Audience Manager提供的技術和後端功能可啟用ID同步。

**使用案例**

根據您的情況，您不一定需要將此設定新增至訪客ID服務程式碼。

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
   <td colname="col2"> <p>您在以下情況下不需要使用此設定： </p> <p> 
     <ul id="ul_4D6F794CD65C43D0BEFBA6F5DE420C2E"> 
      <li id="li_0F048A6AC7BE4450AFA1B20B1AC25808">您透過任何CX Enterprise解決方案使用訪客ID服務，且沒有透過其他資料來源執行ID同步。 在此情況下，您的帳戶擁有 ID 0 的預設容器，且不需要採取任何行動。 </li> 
      <li id="li_5657D64D9406407D9B4DB7D8BE4F8EE4">您的所有資料來源都在單一容器內。 </li> 
     </ul> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>需要</b> </p> </td> 
   <td colname="col2"> <p>當以下所有條件都適用時，您需要使用此設定： </p> <p> 
     <ul id="ul_9AFD14FC5A2745F7BD7BE7B64545DA62"> 
      <li id="li_04F0EFBBD71B43608CAAA7E7409D33FE">您沒有使用 <span class="keyword">Audience Manager</span>。 </li> 
      <li id="li_4BFA6DC76CE9455EBBC337FD2FE820BF">您需要將 ID 與容器所組織的其他資料來源同步。 </li> 
      <li id="li_731DA5D1CBF244F8BEBE57C0E2EBA713">您需要將 ID 與您的網域的不同頁面上的不同容器中的資料來源同步。 </li> 
     </ul> </p> </td> 
  </tr> 
 </tbody> 
</table>

## 當您使用DIL和`VisitorAPI.js`時設定容器ID {#section-f283cb69c8de4348b5316cc4e02a3e9e}

如果您已在相同頁面上部署[!UICONTROL DIL] *和* `VisitorAPI.js`：

* 若為ID同步，訪客ID服務程式碼會優先於DIL。
* 僅設定訪客ID服務程式碼中的`idSyncContainerID`組態。

