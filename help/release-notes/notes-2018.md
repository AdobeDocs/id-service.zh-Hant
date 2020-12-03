---
description: 2018 年 Experience Cloud Identity 服務的功能發佈、更新或變更。
keywords: ID Service
seo-description: 2018 年 Experience Cloud Identity 服務的功能發佈、更新或變更。
seo-title: 2018 年發行說明
title: 2018 年發行說明
uuid: 771b5b11-a8e3-464c-b65e-b15135584ace
translation-type: tm+mt
source-git-commit: e6d65f1bfed187d7440512e8f3c2de0550506c95
workflow-type: tm+mt
source-wordcount: '489'
ht-degree: 39%

---


# 2018 年發行說明 {#release-notes}

2018 年 Experience Cloud Identity 服務的功能發佈、更新或變更。

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
   <td colname="col1"> <p>提高AMCV Cookie的安全性 </p> </td> 
   <td colname="col2"> <p>在內部安全掃描期間，發現當使用DTM程式庫時，用於作業管理的Cookie無法指定正確的屬性。 這可能導致Cookie資訊不慎共用。 為解決此問題，我們引入了允許客戶將AMCV Cookie設為安全的組態。 請參閱 <a href="/help/library/function-vars/securecookie.md" format="https" scope="external">secureCookie</a>。 </p> </td> 
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
   <td colname="col1"> <p>提高AMCV Cookie的安全性 </p> </td> 
   <td colname="col2"> <p>在內部安全掃描期間，發現當使用DTM程式庫時，用於作業管理的Cookie無法指定正確的屬性。 這可能導致Cookie資訊不慎共用。 為解決此問題，我們引入了允許客戶將AMCV Cookie設為安全的組態。 請參閱 secureCookie。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>整合程式碼和ID必須是數字或非空字串 </p> </td> 
   <td colname="col2"> <p>修正當資料包含非數字或非空字串的整合「code」或「id」時，驗證「setCustomerIDs」的問題。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> ECID JS可在Public Git repo中使用 </td> 
   <td colname="col2"> 公開 Git 存放庫現於 https://github.com/Adobe-Marketing-Cloud/id-service/releases ，開放所有 Experience Cloud 客戶使用 ECID JS。 </td> 
  </tr> 
 </tbody> 
</table>

## 版本 3.1.2 {#section-3cba186f74fe4f2186a9ca2e5e0a2514}

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
   <td colname="col2"> <p>Experience Cloud Identity Service 3.1.0 版發行後，我們發現實作本版本時，不重複訪客計數會出現與事實不符的尖峰。此行為只會與最新版ECID v3.1.0一起呈現，而且如果使用者在Safari瀏覽器的隱私權設定中選取「僅允許從目前網站使用」選項，則會顯示。 3.1.2版修正了此問題。 </p> </td> 
  </tr> 
 </tbody> 
</table>

## 版本 3.1.0 {#section-a20c8278bf9643018965330415091e53}

>[!NOTE]
>
>建議您盡快從 3.1.0 版升級至最新版本。請參閱 3.1.2 版說明。Adobe Experience Platform Launch、DTM 及 AppMeasurement 都會提供最新套件。

<table id="table_512039AFC4D34038B8F116B71EEEE7F6"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> 項目說明 </th> 
   <th colname="col2" class="entry"> </th> 
  </tr>
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p>在不正確的網域上設定Cookie </p> </td> 
   <td colname="col2"> <p>我們修正臨時訪客Cookie在「預設」Cookie網域中設定Cookie，而非在設定(initConfig)中提供的網域中設定Cookie的錯誤。 </p> </td> 
  </tr> 
 </tbody> 
</table>

## 版本 3.0 {#section-5fcaef66e8b343238abeb10048dc5747}

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
   <td colname="col2"> <p><b>Iframe</b> </p> <p>對於執行多個ID同步的客戶，由於持續進行CPU計算，UI在某些情況下會遭到封鎖。 我們推出線程產生功能，將ID同步請求分隔為100毫秒。 </p> <p>這項變更將改善使用Visitor 2.3.0+和DIL 6.10+的客戶的效能。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 新增停用第三方呼叫的功能 </td> 
   <td colname="col2"> <p><b>JavaScript - 3.0.0</b> </p> <p>Adobe 重新命名下列用以允許停用第三方同步呼叫的設定。 </p> <p>idSyncDisableSyncs 重新命名為 disableIdSyncs </p> <p>idSyncDisable3rdPartySyncing 重新命名為 disableThirdPartyCookies </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>Internet Explorer支援 </p> </td> 
   <td colname="col2"> <p>ID服務不再支援Internet Explorer 6、7、8和9。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>更新至 getInstance 文件 </p> </td> 
   <td colname="col2"> <p>新增勿以 var visitor = new Visitor 將 Visitor 函式具現化的警告訊息。 </p> </td> 
  </tr> 
 </tbody> 
</table>

