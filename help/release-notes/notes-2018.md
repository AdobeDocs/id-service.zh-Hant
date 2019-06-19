---
description: 2018年Experience Platform Identity Service的功能發行、更新或變更。
keywords: ID 服務
seo-description: 2018年Experience Platform Identity Service的功能發行、更新或變更。
seo-title: 2018 年發行說明
title: 2018 年發行說明
uuid: 771b5b11-a8 e3-464c-b65 e-b15135584 ACE
translation-type: tm+mt
source-git-commit: 746f8937c59d318dcf7245c7f8484884974601dc

---


# 2018 年發行說明 {#release-notes}

2018年Experience Platform Identity Service的功能發行、更新或變更。

## 3.3 版 {#section-3202c8d5457a45a5b5f4b4c838d44de3}

<table id="table_201417BD540E4EE69911AABE9BF77509"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> 項目說明 </th> 
   <th colname="col2" class="entry"> </th> 
  </tr>
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p>提高了 AMCV Cookie 的安全性 </p> </td> 
   <td colname="col2"> <p>在內部安全性掃描期間，發現當使用 DTM 資料庫時，會發生用於工作階段管理的 Cookie 無法指定正確屬性的情況。這可能會導致 Cookie 資訊不慎遭共用。為解決此問題，我們已推出一項設定，可讓客戶將 AMCV Cookie 設為安全 Cookie。請參閱 <a href="/help/library/function-vars/securecookie.md" format="https" scope="external">secureCookie</a>。 </p> </td> 
  </tr> 
 </tbody> 
</table>

## 3.2 版 {#section-ae2fee1c152e405faa4eb395f960e2f6}

<table id="table_6546F5C74E4742E4B5E9793BCEAB66FA"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> 項目說明 </th> 
   <th colname="col2" class="entry"> </th> 
  </tr>
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p>提高了 AMCV Cookie 的安全性 </p> </td> 
   <td colname="col2"> <p>在內部安全性掃描期間，發現當使用 DTM 資料庫時，會發生用於工作階段管理的 Cookie 無法指定正確屬性的情況。這可能會導致 Cookie 資訊不慎遭共用。為解決此問題，我們已推出一項設定，可讓客戶將 AMCV Cookie 設為安全 Cookie。請參閱 secureCookie。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>整合代碼和 ID 必須為數字或非空白的字串 </p> </td> 
   <td colname="col2"> <p>修正含有非數字或非空白字串集合「代碼」或「ID」的資料，在驗證「setCustomerIDs」時出現的問題。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 公開 Git 存放庫提供 ECID JS </td> 
   <td colname="col2"> 公開 Git 存放庫現於 https://github.com/Adobe-Marketing-Cloud/id-service/releases，開放所有 Experience Cloud 客戶使用 ECID JS。 </td> 
  </tr> 
 </tbody> 
</table>

## 3.1.2 版 {#section-3cba186f74fe4f2186a9ca2e5e0a2514}

<table id="table_9FA4E20C996746A2A4219C9A0F759AD1"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> 項目說明 </th> 
   <th colname="col2" class="entry"> </th> 
  </tr>
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p>不重複訪客計數出現不符實情的尖峰 </p> </td> 
   <td colname="col2"> <p>在Experience Platform Identity Service3.1.0發行後，我們發現在實施此版本時，獨特訪客計數中會產生不真實的尖峰。只有在最新版的 ECID v3.1.0，而且使用者在 Safari 瀏覽器的隱私權設定中選取「僅允許來自目前的網站」時，才會發生此問題。3.1.2 版會修正此問題。 </p> </td> 
  </tr> 
 </tbody> 
</table>

## 3.1.0 版 {#section-a20c8278bf9643018965330415091e53}

>[!NOTE]
>
>建議您在最早的時間，從3.1.0版升級至最新版本。請參閱 3.1.2 版說明。Adobe Launch、DTM 及 AppMeasurement 都會提供最新套件。

<table id="table_512039AFC4D34038B8F116B71EEEE7F6"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> 項目說明 </th> 
   <th colname="col2" class="entry"> </th> 
  </tr>
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p>Cookie 設定在不正確的網域 </p> </td> 
   <td colname="col2"> <p>我們修正的問題是暫時訪客 Cookie 會將 Cookie 設在「預設」Cookie 網域，而非設於組態 (initConfig) 中提供的網域。 </p> </td> 
  </tr> 
 </tbody> 
</table>

## 3.0 版 {#section-5fcaef66e8b343238abeb10048dc5747}

<table id="table_7E9224D6CC924A2DB5119171C9DC5443"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> 項目說明 </th> 
   <th colname="col2" class="entry"> </th> 
  </tr>
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p>適用於多重 ID 同步請求的執行緒禮讓作業 </p> </td> 
   <td colname="col2"> <p><b>Iframe</b> </p> <p>若為執行多重 ID 同步的客戶，由於執行連續 CPU 運算，因此導致 UI 在某些情況下發生壅塞情況。我們推出了執行緒禮讓作業，藉此按照每個執行緒 100 毫秒的頻率隔離 ID 同步請求。 </p> <p>這項變革改善了使用 Visitor 2.3.0+ 與 DIL 6.10+ 之客戶的效能。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 新增停用第三方呼叫的功能 </td> 
   <td colname="col2"> <p><b>JavaScript - 3.0.0</b> </p> <p>Adobe 重新命名下列用以允許停用第三方同步呼叫的設定。 </p> <p>idSyncDisableSyncs 重新命名為 disableIdSyncs </p> <p>idSyncDisable3rdPartySyncing 重新命名為 disableThirdPartyCookies </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>Internet Explorer 支援 </p> </td> 
   <td colname="col2"> <p>ID 服務不再支援 Internet Explorer 6、7、8 和 9。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>更新至 getInstance 文件 </p> </td> 
   <td colname="col2"> <p>新增勿以 var visitor = new Visitor 將 Visitor 函式具現化的警告訊息。 </p> </td> 
  </tr> 
 </tbody> 
</table>

