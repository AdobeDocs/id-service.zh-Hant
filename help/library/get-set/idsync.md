---
description: idSyncByURL 和 idSyncByDataSource 這兩個 ID 服務函數可讓您在 Destination Publishing iFrame 中手動實作 ID 同步。VisitorAPI.js 1.10 (含) 以上版本均已提供這些函數。
keywords: ID 服務
title: 依 URL 或資料來源執行 ID 同步作業
exl-id: a22e6b47-00ff-4b51-9958-ddeccc1e507e
source-git-commit: cb89ac70e37f35d5e4e2b971f2df9645304522f8
workflow-type: tm+mt
source-wordcount: '236'
ht-degree: 96%

---

# 依 URL 或資料來源執行 ID 同步作業{#id-synchronization-by-url-or-data-source}

idSyncByURL 和 idSyncByDataSource 這兩個 ID 服務函數可讓您在 Destination Publishing iFrame 中手動實作 ID 同步。VisitorAPI.js 1.10 (含) 以上版本均已提供這些函數。

## 語法、屬性和巨集 {#section-90ac61617482463aaf4c57009b830332}

**語法**

<table id="table_ADC7501511914805A6A6B24B2DFEBA51"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> 程式碼 </th> 
   <th colname="col2" class="entry"> 同步用戶 ID </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr valign="top"> 
   <td colname="col1"> <p> <span class="codeph"> visitor.idSyncByURL(); </span> </p> </td> 
   <td colname="col2"> <p>在不同的資料合作夥伴和 <span class="keyword">Audience Manager</span> 之間，使用自訂 ID 同步 URL。 </p> </td> 
  </tr> 
  <tr valign="top"> 
   <td colname="col1"> <p> <span class="codeph"> visitor.idSyncByDataSource(); </span> </p> </td> 
   <td colname="col2"> <p>已知 DPID 和 DPUUID，並想使用標準 ID 同步 URL 格式將其傳送給 <span class="keyword">Audience Manager</span>。 </p> <p></p> </td> 
  </tr> 
 </tbody> 
</table>

**屬性**

下表羅列及定義了兩個函數皆可使用的屬性。

<table id="table_5343BE784E694C67B09A0A8878CF8001"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> 名稱 </th> 
   <th colname="col2" class="entry"> 類型 </th> 
   <th colname="col3" class="entry"> 說明 </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr valign="top"> 
   <td colname="col1"> <span class="codeph"> dpid </span> </td> 
   <td colname="col2"> 字串 </td> 
   <td colname="col3"> <p>Audience Manager 指派的資料提供者 ID。 </p> </td> 
  </tr> 
  <tr valign="top"> 
   <td colname="col1"> <span class="codeph"> dpuuid </span> </td> 
   <td colname="col2"> 字串 </td> 
   <td colname="col3"> <p>資料提供者獨一無二的用戶 ID。 </p> </td> 
  </tr> 
  <tr valign="top"> 
   <td colname="col1"> <span class="codeph"> minutesToLive </span> </td> 
   <td colname="col2"> 數字 </td> 
   <td colname="col3"> <p> <i>(選用)</i> 設定 Cookie 過期時間。值必須是整數。預設值為 20160 分鐘 (14天)。 </p> </td> 
  </tr> 
  <tr valign="top"> 
   <td colname="col1"> <span class="codeph"> url </span> </td> 
   <td colname="col2"> 字串 </td> 
   <td colname="col3"> <p>目的地 URL。 </p> </td> 
  </tr> 
 </tbody> 
</table>

**巨集**

這兩個函數都接受以下巨集：

* `%TIMESTAMP%`：產生時間戳記 (單位為毫秒)。用於快取破壞。
* `%DID%`：插入用戶的 Audience Manager ID。
* `%HTTP_PROTO%`；設定通訊協定 (`http` 或 `https`)。

## 範常式式碼和輸出 {#section-0115615c37584a19a2ab11e917c4e7e9}

如果執行成功，兩個函數會傳回 `Successfully queued`。如果失敗則傳回錯誤訊息字串。

### visitor.idSyncByURL

**範例程式碼**

```javascript
   //Instatiate Visitor
    var visitor = Visitor.getInstance
    ("MARKETING-CLOUD-ORG-ID-HERE",{}); 
   // Fires url with macros replaced 
    visitor.idSyncByURL({ 
    dpid: '24', // must be a string 
    url: '//su.addthis.com/red/usync?pid=16&puid=%DID%&url=%HTTP_PROTO%://
    dpm.demdex.net/ibs:dpid=420&dpuuid={{uid}}', 
    minutesToLive: 20160 // optional, defaults to 20160 minutes (14 days) });
```

**範例輸出**

```
http://su.addthis.com/red/usync?pid=16&puid=28777806459181003670799219185178493848&url=http%3A%2F%2Fdpm.demdex.net%2Fibs%3Adpid%3D420%26dpuuid%3D%7B%7Buid%7D%7D
```

### visitor.idSyncByDataSource

**範例程式碼**

```javascript
  //Instantiate Visitor
   var visitor = Visitor.getInstance
   ("MARKETING-CLOUD-ORG-ID-HERE",{}); 
  // Fires 'http:/https:' + '//dpm.demdex.net/ibs:dpid=&dpuuid='
   visitor.idSyncByDataSource({ 
     dpid: '24', // must be a string
     dp     minutesToLive: 20160 // optional, defaults to 20160 minutes (14 days) });
```

**範例輸出**

```
http://dpm.demdex.net/ibs:dpid=24&dpuuid=98765
```

>[!MORELIKETHIS]
>
>* [DIL idSync](https://experienceleague.adobe.com/docs/audience-manager/user-guide/dil-api/dil-instance-methods.html?lang=zh-Hant#idsync)
