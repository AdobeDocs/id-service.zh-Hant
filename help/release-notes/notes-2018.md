---
description: 2018 年 Experience Cloud Identity 服務的功能發佈、更新或變更。
keywords: ID 服務
seo-description: 2018 年 Experience Cloud Identity 服務的功能發佈、更新或變更。
seo-title: 2018 年版本注意事項
title: 2018 年版本注意事項
uuid: 771b5b11-a8e3-464c-b65e-b15135584ace
exl-id: ad3cccf1-2753-4ac9-a68c-15b2d62bbc1a
translation-type: ht
source-git-commit: 4453ebf701ea2dc06e6093dd77be6eb0f3b2936e
workflow-type: ht
source-wordcount: '491'
ht-degree: 100%

---

# 2018 年版本注意事項 {#release-notes}

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
   <td colname="col1"> <p>提升 AMCV Cookie 的安全性 </p> </td> 
   <td colname="col2"> <p>在內部安全性掃描期間，我們發現當使用 DTM 程式庫時，用於作業階段管理的 Cookie 無法指定適當的屬性。這可能會導致 Cookie 資訊無意間被分享。為了解決此問題，我們引進了一項設定，可讓客戶將 AMCV Cookie 設定為安全 Cookie。請參閱 <a href="/help/library/function-vars/securecookie.md" format="https" scope="external">secureCookie</a>。 </p> </td> 
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
   <td colname="col1"> <p>提升 AMCV Cookie 的安全性 </p> </td> 
   <td colname="col2"> <p>在內部安全性掃描期間，我們發現當使用 DTM 程式庫時，用於作業階段管理的 Cookie 無法指定適當的屬性。這可能會導致 Cookie 資訊無意間被分享。為了解決此問題，我們引進了一項設定，可讓客戶將 AMCV Cookie 設定為安全 Cookie。請參閱 secureCookie。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>整合代碼和 ID 必須是數字或非空白字串 </p> </td> 
   <td colname="col2"> <p>已修正當資料包含非數字或非空白字串的整合「代碼」或「ID」時，驗證「setCustomerIDs」時所發生的問題。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 公開 Git 存放庫中有提供 ECID JS </td> 
   <td colname="col2"> 公開 Git 存放庫現於 https://github.com/Adobe-Marketing-Cloud/id-service/releases，開放所有 Experience Cloud 客戶使用 ECID JS。 </td> 
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
   <td colname="col2"> <p>Experience Cloud Identity Service 3.1.0 版發行後，我們發現實作本版本時，不重複訪客計數會出現與事實不符的尖峰。只有在使用最新版 ECID v3.1.0 而且用戶已在 Safari 瀏覽器的隱私設定中選取「僅允許來自目前網站」選項時，才會出現這個行為。版本 3.1.2 解決了這個問題。 </p> </td> 
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
   <td colname="col1"> <p>在不正確的網域中設定 Cookie </p> </td> 
   <td colname="col2"> <p>我們已修正暫時訪客 Cookie 在「預設」Cookie 網域中設定 Cookie，而不是在設定 (initConfig) 提供的網域中設定 Cookie 的錯誤。 </p> </td> 
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
   <td colname="col2"> <p><b>Iframe</b> </p> <p>如果客戶正在執行多個 ID 同步作業，則因為持續進行 CPU 計算，所以在某些情況下會導致 UI 遭到封鎖。我們即將推出執行緒讓步，以便分隔 ID 同步要求 (每個要求 100 毫秒)。 </p> <p>這項變更將會讓使用 Visitor 2.3.0+ 和 DIL 6.10+ 的客戶提高效能。 </p> </td> 
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
