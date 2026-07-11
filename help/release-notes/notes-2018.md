---
description: 2018年訪客ID服務的功能發佈、更新或變更。
keywords: 訪客 ID 服務
title: 2018 年版本注意事項
exl-id: ad3cccf1-2753-4ac9-a68c-15b2d62bbc1a
TQID: https://experienceleague.adobe.com/1vrVFuFbQiLL9XYnZwEf0WkElW-qhsklHbrem-mo5LE
product_v2: id: e1971122-7081-4556-9222-8a31bd71800c
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554id: c66ffd68-0f65-42bb-aa23-b4020f12e0bdid: f8a45b24-4be7-4f1b-909b-60d06b483a20id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2: id: c2be0313-b3ae-45e0-b454-d20bf54b23f2id: d095671a-1355-40aa-8b5f-06c33c68080bid: f4e6943a-c91a-4134-a2c7-f4f20cfff2f0
source-git-commit: 09ee359440c122702a6ce83708c98af3862c9cc9
workflow-type: tm+mt
source-wordcount: 488
ht-degree: 66%

---

# 2018 年版本注意事項 {#release-notes}

2018年訪客ID服務的功能發佈、更新或變更。

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
   <td colname="col2"> <p>在內部安全性掃描期間，發現用於工作階段管理的Cookie無法指定適當的屬性。 這可能會導致 Cookie 資訊無意間被分享。 為了解決此問題，我們引進了一項設定，可讓客戶將 AMCV Cookie 設定為安全 Cookie。 請參閱 <a href="/help/library/function-vars/securecookie.md" format="https" scope="external">secureCookie</a>。 </p> </td> 
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
   <td colname="col2"> <p>在內部安全性掃描期間，發現用於工作階段管理的Cookie無法指定適當的屬性。 這可能會導致 Cookie 資訊無意間被分享。 為了解決此問題，我們引進了一項設定，可讓客戶將 AMCV Cookie 設定為安全 Cookie。 請參閱 secureCookie。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>整合代碼和 ID 必須是數字或非空白字串 </p> </td> 
   <td colname="col2"> <p>已修正當資料包含非數字或非空白字串的整合「代碼」或「ID」時，驗證「setCustomerIDs」時所發生的問題。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 公開 Git 存放庫中有提供 ECID JS </td> 
   <td colname="col2"> 公開Git存放庫現於https://github.com/Adobe-Marketing-Cloud/id-service/releases ，開放所有CX Enterprise客戶使用ECID JS。 </td> 
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
   <td colname="col2"> <p>訪客ID服務3.1.0版發行後，我們發現實作本版本時，不重複訪客計數會出現與事實不符的尖峰。 只有在使用最新版 ECID v3.1.0 而且用戶已在 Safari 瀏覽器的隱私設定中選取「僅允許來自目前網站」選項時，才會出現這個行為。 版本 3.1.2 解決了這個問題。 </p> </td> 
  </tr> 
 </tbody> 
</table>

## 3.1.0 版 {#section-a20c8278bf9643018965330415091e53}

>[!NOTE]
>
>建議您盡快從 3.1.0 版升級至最新版本。 請參閱 3.1.2 版說明。 標籤和AppMeasurement中提供最新套件。

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
   <td colname="col2"> <p>我們已修正暫時訪客Cookie在「預設」Cookie網域中設定Cookie，而非在設定(initConfig)中提供的網域中設定的錯誤。 </p> </td> 
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
   <td colname="col2"> <p><b>Iframe</b> </p> <p>如果客戶正在執行多個 ID 同步作業，則因為持續進行 CPU 計算，所以在某些情況下會導致 UI 遭到封鎖。 我們即將推出執行緒讓步，以便分隔 ID 同步要求 (每個要求 100 毫秒)。 </p> <p>這項變更將會讓使用 Visitor 2.3.0+ 和 DIL 6.10+ 的客戶提高效能。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 新增停用第三方呼叫的功能 </td> 
   <td colname="col2"> <p><b>JavaScript - 3.0.0</b> </p> <p>Adobe 重新命名下列用以允許停用第三方同步呼叫的設定。 </p> <p>idSyncDisableSyncs 重新命名為 disableIdSyncs </p> <p>idSyncDisable3rdPartySyncing 重新命名為 disableThirdPartyCookies </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>Internet Explorer 支援 </p> </td> 
   <td colname="col2"> <p>訪客ID服務不再支援Internet Explorer 6、7、8和9。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>更新至 getInstance 文件 </p> </td> 
   <td colname="col2"> <p>新增勿以 var visitor = new Visitor 將 Visitor 函式具現化的警告訊息。 </p> </td> 
  </tr> 
 </tbody> 
</table>

