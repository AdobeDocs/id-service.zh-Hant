---
description: idSyncByURL 和 idSyncByDataSource 這兩個 ID 服務函數可讓您在 Destination Publishing iFrame 中手動實施 ID 同步。這兩個函數適用於 VisitorAPI.js 1.10 版或更新版本。
keywords: ID 服務
seo-description: idSyncByURL 和 idSyncByDataSource 這兩個 ID 服務函數可讓您在 Destination Publishing iFrame 中手動實施 ID 同步。這兩個函數適用於 VisitorAPI.js 1.10 版或更新版本。
seo-title: 依 URL 或資料來源執行 ID 同步作業
title: 依 URL 或資料來源執行 ID 同步作業
uuid: ff83d910-8375-4295-9f2a-e14c15eee09a
translation-type: ht
source-git-commit: bb687c1cd14aae7faef2565dcf9d041a1c06e3bd

---


# 依 URL 或資料來源執行 ID 同步作業{#id-synchronization-by-url-or-data-source}

idSyncByURL 和 idSyncByDataSource 這兩個 ID 服務函數可讓您在 Destination Publishing iFrame 中手動實施 ID 同步。這兩個函數適用於 VisitorAPI.js 1.10 版或更新版本。

內容:

<ul class="simplelist"> 
 <li> <a href="../../mcvid-library/mcvid-get-set/mcvid-idsync.md#section-90ac61617482463aaf4c57009b830332" format="dita" scope="local"> 語法、屬性和巨集 </a> </li> 
 <li> <a href="../../mcvid-library/mcvid-get-set/mcvid-idsync.md#section-0115615c37584a19a2ab11e917c4e7e9" format="dita" scope="local"> 範例程式碼和輸出 </a> </li> 
</ul>

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
   <td colname="col2"> <p>在不同的資料合作夥伴和 <span class="keyword">Audience Manager</span> 之間，使用自訂 ID 同步 URL。 </p> <p> 
     <draft-comment>
       不同資料合作夥伴和 Audience Manager 之間。例如，合作夥伴 x 會用來與合作夥伴 y 同步使用者 ID，然後再將該使用者 ID 傳送給 Audience Manager。 
     </draft-comment> </p> </td> 
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

* ** `%TIMESTAMP%`: **產生時間戳記 (單位為毫秒)。用於快取破產。
* ** `%DID%`: **插入使用者的 Audience Manager ID。
* ** `%HTTP_PROTO%`: **設定通訊協定 (`http` 或 `https`)。

## 範例程式碼和輸出 {#section-0115615c37584a19a2ab11e917c4e7e9}

如果執行成功，兩個函數會傳回 `Successfully queued`。如果失敗則傳回錯誤訊息字串。

**visitor.idSyncByURL**

<table id="table_56AD8291DF9445C69CC2BF50435E1626"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> 範例程式碼 </th> 
   <th colname="col2" class="entry"> 範例輸出 </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <code class="syntax javascript"> //Instatiate Visitor 
      var visitor = Visitor.getInstance("MARKETING-CLOUD-ORG-ID-HERE",{});

    //&amp;nbsp;Fires&amp;nbsp;url&amp;nbsp;with&amp;nbsp;macros&amp;nbsp;replaced
    visitor.idSyncByURL({
    &amp;nbsp;dpid:&amp;nbsp;&#39;24&#39;,&amp;nbsp;//&amp;nbsp;must&amp;nbsp;be&amp;nbsp;a&amp;nbsp;string
    &amp;nbsp;url:&amp;nbsp;&#39;//su.addthis.com/red/usync?pid=16&amp;amp;puid=%DID%&amp;amp;url=%HTTP_PROTO%%3A%2F%2Fdpm.demdex.net%2Fibs%3Adpid%3D420%26dpuuid%3D%7B%7Buid%7D%7D&#39;,
    &amp;nbsp;minutesToLive:&amp;nbsp;20160&amp;nbsp;//&amp;nbsp;optional,&amp;nbsp;defaults&amp;nbsp;to&amp;nbsp;20160&amp;nbsp;minutes&amp;nbsp;(14&amp;nbsp;days)&amp;nbsp;
    }); &lt;/code&gt; &lt;/p&gt; &lt;/td&gt;
<td colname="col2"> <p> <span class="codeph"> http://su.addthis.com/red/usync?pid=16&amp;puid=28777806459181003670799219185178493848&amp;url=http%3A%2F%2Fdpm.demdex.net%2Fibs%3Adpid%3D420%26dpuuid%3D%7B%7Buid%7D%7D </span> </p> </td> 
  </tr> 
 </tbody> 
</table>

**visitor.idSyncByDataSource**

<table id="table_90D61A7E715D47238AAFF2808B33C2F0"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> 範例程式碼 </th> 
   <th colname="col2" class="entry"> 範例輸出 </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <code class="syntax javascript"> //Instantiate Visitor 
      var visitor = Visitor.getInstance("MARKETING-CLOUD-ORG-ID-HERE",{});

    //&amp;nbsp;Fires&amp;nbsp;&#39;http:/https:&#39;&amp;nbsp;+&amp;nbsp;&#39;//dpm.demdex.net/ibs:dpid=&amp;lt;dpid&amp;gt;&amp;amp;dpuuid=&amp;lt;dpuuid&amp;gt;&#39;
    visitor.idSyncByDataSource({
    &amp;nbsp;dpid:&amp;nbsp;&#39;24&#39;,&amp;nbsp;//&amp;nbsp;must&amp;nbsp;be&amp;nbsp;a&amp;nbsp;string
    &amp;nbsp;dpuuid:&amp;nbsp;&#39;98765&#39;,&amp;nbsp;//&amp;nbsp;must&amp;nbsp;be&amp;nbsp;a&amp;nbsp;string
    &amp;nbsp;minutesToLive:&amp;nbsp;20160&amp;nbsp;//&amp;nbsp;optional,&amp;nbsp;defaults&amp;nbsp;to&amp;nbsp;20160&amp;nbsp;minutes&amp;nbsp;(14&amp;nbsp;days)&amp;nbsp;
    }); &lt;/code&gt; &lt;/p&gt; &lt;/td&gt;
<td colname="col2"> <p> <span class="codeph"> http://dpm.demdex.net/ibs:dpid=24&amp;dpuuid=98765 </span> </p> </td> 
  </tr> 
 </tbody> 
</table>

>[!MORE_LIKE_THIS]
>
>* [DIL idSync](https://marketing.adobe.com/resources/help/zh_TW/aam/r_dil_idsync.html)

