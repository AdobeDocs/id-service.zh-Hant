---
description: 這是非同步 API，依預設會為 Analytics、ID 服務、資料收集退出、地理位置以及中繼資料「blob」內容傳回識別碼。您也可以透過選擇性的 visitor.FIELDS 列舉控制您要傳回的 ID。
keywords: ID 服務
seo-description: 這是非同步 API，依預設會為 Analytics、ID 服務、資料收集退出、地理位置以及中繼資料「blob」內容傳回識別碼。您也可以透過選擇性的 visitor.FIELDS 列舉控制您要傳回的 ID。
seo-title: getVisitorValues
title: getVisitorValues
uuid: 7fb831b3-cf7e-40e2-a219-07fec28ad49c
translation-type: ht
source-git-commit: e6d65f1bfed187d7440512e8f3c2de0550506c95

---


# getVisitorValues{#getvisitorvalues}

這是非同步 API，依預設會為 Analytics、ID 服務、資料收集退出、地理位置以及中繼資料「blob」內容傳回識別碼。您也可以透過選擇性的 visitor.FIELDS 列舉控制您要傳回的 ID。

內容:

<ul class="simplelist"> 
 <li> <a href="../../library/get-set/getvisitorvalues.md#section-5aebe3907b2b46e997f45a1d1ed35c09" format="dita" scope="local"> 語法 </a> </li> 
 <li> <a href="../../library/get-set/getvisitorvalues.md#section-36a31683558742a5915db3a391e09f7b" format="dita" scope="local"> 使用案例 1: 要求預設資料集 </a> </li> 
 <li> <a href="../../library/get-set/getvisitorvalues.md#section-467b2f4e513344c89b7332b05f6f59f3" format="dita" scope="local"> 使用案例 2: 要求自訂資料集 </a> </li> 
 <li> <a href="../../library/get-set/getvisitorvalues.md#section-4c4c300167694c6fbff1d6c612f372b5" format="dita" scope="local"> 已定義的回應參數 </a> </li> 
</ul>

## 語法 {#section-5aebe3907b2b46e997f45a1d1ed35c09}

此函數使用下列語法 (斜體部分代表變數預留位置): ` var *`values`* = visitor.getVisitorValues (callback, [visitor.FIELDS. *`ID type`*, visitor.FIELDS. *`ID type`*]);`

在函數參數中:

* ` *`callback`*` 代表您擁有的回呼程式碼，此程式碼用於接收傳回的 ID。
* *(Optional)* ` visitor.FIELDS. *`ID type`*` 是列舉，可讓您指定想要此函數傳回的 [ID 值](../../library/get-set/getvisitorvalues.md#section-4c4c300167694c6fbff1d6c612f372b5)。

請參閱以下所使用的案例和定義，以瞭解更多詳細資訊。

## 使用案例 1: 要求預設資料集 {#section-36a31683558742a5915db3a391e09f7b}

此程式碼會傳回標準的資料集。您的要求和回應看起來可能類似於下列範例。

```js
//Call the ID service 
var visitor = Visitor.getInstance ("Insert Experience Cloud organization ID here",{...}); 
   
//Add your callback to the GET method to return IDs and data. 
visitor.getVisitorValues(visitorIdsCallback);
```

在預設的範例回應中，某些值已縮短做為示範用途。

```js
//Formatted IDs in JSON response 
{ 
    MCMID: 'mid-1234', 
    MCOPTOUT: 'isoptedout-true', 
    MCAID: 'aid-1234', 
    MCAAMLH: 7, 
    MCAAMB: 'hgfe54236786oygj' 
}
```

## 使用案例 2: 要求自訂資料集 {#section-467b2f4e513344c89b7332b05f6f59f3}

此程式碼使用選用的陣列，以透過 `visitor.FIELDS` 列舉來傳回指定的 ID 集合。在此情況下，我們只需要訪客的 Experience Cloud ID (MCID) 和 Analytics ID (MCAID)。您的要求和回應看起來可能類似於下列範例。

```js
//Call the ID service 
var visitor = Visitor.getInstance("Insert Experience Cloud organization ID here", { ... });

// Add an optional array to specify which IDs you want to return. 
visitor.getVisitorValues(visitorIdsCallback, [visitor.FIELDS.MCMID, visitor.FIELDS.MCAID]);
```

自訂的範例回應只會傳回要求中指定的 ID。

```js
//Formatted IDs in JSON response 
{ 
    MCMID: 'mid-1234', 
    MCAID: 'aid-4321' 
}
```

## 已定義的回應參數 {#section-4c4c300167694c6fbff1d6c612f372b5}

下表列出並定義回應參數。這些也是 `visitor.FIELDS` 列舉中的所有值。請注意，如果特定變數沒有任何值，此方法會傳回空字串。

<table id="table_32D0FEEA76CE4F298EED4B8F5C644232"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> 值 </th> 
   <th colname="col2" class="entry"> 說明 </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> MCAAMB </span> </p> </td> 
   <td colname="col2"> <p>加密的 <span class="keyword">Audience Manager</span> 中繼資料稱為「Blob」。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> MCAAMLH </span> </p> </td> 
   <td colname="col2"> <p>資料收集地區 ID。這是代表特定 ID 服務資料中心之地理位置的數字識別碼。 </p> <p>請參閱 <a href="https://marketing.adobe.com/resources/help/en_US/aam/dcs-regions.html" format="https" scope="external">DCS 地區 ID、位置與主機名稱</a>以及 <a href="../../library/get-set/getlocationhint.md#reference-a761030ff06c4439946bb56febf42d4c" format="dita" scope="local"> getLocationHint </a>。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> MCAID </span> </p> </td> 
   <td colname="col2"> <p>訪客的 <span class="keyword">Analytics</span> ID。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> MCMID </span> </p> </td> 
   <td colname="col2"> <p>訪客的 Experience Cloud ID。 </p> <p>請參閱<a href="../../introduction/cookies.md" format="dita" scope="local"> Cookie 與 Experience Cloud Identity 服務</a>。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> MCOPTOUT </span> </p> </td> 
   <td colname="col2"> <p>表示訪客已選擇退出資料收集的標幟。 </p> <p>這些值包括: </p> <p> 
     <ul id="ul_E82431DE12B449F8822499364B363798"> 
      <li id="li_2BAB7C15A38A408E8FC4B85E70B66E46"> <span class="codeph">‘isoptedout-true'</span>: 訪客已選擇退出資料收集。 </li> 
      <li id="li_BB80AE4CEBC44166BC04428B212FEF51"> <span class="codeph">‘isoptedout-false’</span>: 訪客尚未選擇退出資料收集。 </li> 
     </ul> </p> </td> 
  </tr> 
 </tbody> 
</table>

