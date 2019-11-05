---
description: idSyncByURL 和 idSyncByDataSource 這兩個 ID 服務函數可讓您在 Destination Publishing iFrame 中手動實作 ID 同步。這兩個函數適用於 VisitorAPI.js 1.10 版或更新版本。
keywords: ID 服務
seo-description: idSyncByURL 和 idSyncByDataSource 這兩個 ID 服務函數可讓您在 Destination Publishing iFrame 中手動實作 ID 同步。這兩個函數適用於 VisitorAPI.js 1.10 版或更新版本。
seo-title: 依 URL 或資料來源執行 ID 同步作業
title: 依 URL 或資料來源執行 ID 同步作業
uuid: ff83d910-8375-4295-9f2a-e14c15eee09a
translation-type: ht
source-git-commit: c4c0b791230422f17292b72fd45ba5689a60adae

---


# 依 URL 或資料來源執行 ID 同步作業{#id-synchronization-by-url-or-data-source}

idSyncByURL 和 idSyncByDataSource 這兩個 ID 服務函數可讓您在 Destination Publishing iFrame 中手動實作 ID 同步。這兩個函數適用於 VisitorAPI.js 1.10 版或更新版本。

## 語法、屬性和巨集 {#section-90ac61617482463aaf4c57009b830332}

**語法**

<table id="table_ADC7501511914805A6A6B24B2DFEBA51"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> 程式碼 </th> 
   <th colname="col2" class="entry"> 同步使用者 ID </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr valign="top"> 
   <td colname="col1"> <p> <span class="codeph"> visitor.idSyncByURL(); </span> </p> </td> 
   <td colname="col2"> <p>在不同的資料合作夥伴和 <span class="keyword">Audience Manager</span> 之間，使用自訂 ID 同步 URL。 </p> </td> 
  </tr> 
  <tr valign="top"> 
   <td colname="col1"> <p> <span class="codeph"> visitor.idSyncByDataSource(); </span> </p> </td> 
   <td colname="col2"> <p>已知 DPID 和 DPUUID，並想使用標準 ID 同步 URL 格式將其傳送給 <span class="keyword">Audience Manager</span>。 </p> <p> 
     <draft-comment>
       當您已知使用者 ID 且想傳送給 Audience Manager。 
     </draft-comment> </p> </td> 
  </tr> 
 </tbody> 
</table>

**屬性**

下表列出並定義兩個函數都可使用的屬性。

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
   <td colname="col3"> <p>資料提供者的使用者唯一 ID。 </p> </td> 
  </tr> 
  <tr valign="top"> 
   <td colname="col1"> <span class="codeph"> minutesToLive </span> </td> 
   <td colname="col2"> 數字 </td> 
   <td colname="col3"> <p> <i>(選用)</i> 設定 Cookie 過期時間。必須是整數。預設為 20160 分鐘 (14 天)。 </p> </td> 
  </tr> 
  <tr valign="top"> 
   <td colname="col1"> <span class="codeph"> url </span> </td> 
   <td colname="col2"> 字串 </td> 
   <td colname="col3"> <p>目標 URL。 </p> </td> 
  </tr> 
 </tbody> 
</table>

**巨集**

兩個函數都接受下列巨集:

* `%TIMESTAMP%`: 產生時間戳記 (單位為毫秒)。用於快取破產。
* `%DID%`: 插入使用者的 Audience Manager ID。
* `%HTTP_PROTO%`: 設定通訊協定 (`http` 或 `https`)。

## 範例程式碼和輸出 {#section-0115615c37584a19a2ab11e917c4e7e9}

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
     dpuuid: '98765', // must be a string 
     minutesToLive: 20160 // optional, defaults to 20160 minutes (14 days) });
```

**範例輸出**

```
http://dpm.demdex.net/ibs:dpid=24&dpuuid=98765
```

>[!MORELIKETHIS]
>
>* [DIL idSync](https://docs.adobe.com/content/help/zh-Hant/audience-manager/user-guide/dil-api/dil-instance-methods.html#idsync)

