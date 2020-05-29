---
description: 在您部署訪客 ID 服務後，在 Analytics 中有 5 種方式可用來識別訪客。
keywords: ID Service
seo-description: 在您部署訪客 ID 服務後，在 Analytics 中有 5 種方式可用來識別訪客。
seo-title: Analytics ID 的作業順序
title: Analytics ID 的作業順序
uuid: cb1d136e-093f-43b0-a7e1-96f1e61fdad0
translation-type: ht
source-git-commit: d2bc0e7fedc4e48d51f5dad158f9f8bfcb0cb4f3
workflow-type: ht
source-wordcount: '329'
ht-degree: 100%

---


# Analytics ID 的作業順序{#order-of-operations-for-analytics-ids}

在您部署訪客 ID 服務後，在 Analytics 中有 5 種方式可用來識別訪客。

在許多情況下，您可能會在一個呼叫中看見 2 或 3 個不同的 ID，但 Analytics 將會使用清單中第一個出現的 ID 做為正式的 [!DNL Experience Cloud] ID。例如，如果您設定自訂訪客 ID (放在 `vid` 查詢參數中)，系統將使用該 ID 而非同一點擊出現的其他 ID。請參閱[設定 Analytics 與 Experience Cloud ID](../../reference/analytics-reference/analytics-ids.md#concept-f381dd18ee184c6c8e48286937a161d6) 以取得更多資訊。

<table id="table_D267D36451F643D1BB68AF6FEAA6AD1A"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> 使用順序 </th> 
   <th colname="col2" class="entry"> 查詢參數 (收集方法) </th> 
   <th colname="col3" class="entry"> 使用時機 </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <b>第 1<sup></sup></b> </p> </td> 
   <td colname="col2"> <p> <a href="https://docs.adobe.com/content/help/zh-Hant/analytics/implementation/vars/config-vars/visitorid.html" format="http" scope="external"> vid (s.visitorID)</a> </p> </td> 
   <td colname="col3"> <p>已設定 <span class="codeph">s.visitorID</span>。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>第 2<sup></sup></b> </p> </td> 
   <td colname="col2"> <p> <a href="https://docs.adobe.com/content/help/zh-Hant/core-services/interface/ec-cookies/cookies-analytics.html" format="http" scope="external"> aid (s_vi Cookie)</a> </p> </td> 
   <td colname="col3"> <p>在您部署 <span class="keyword">Experience Cloud</span> ID 服務之前訪客已有 s_vi Cookie，或是您已設定<a href="../../reference/analytics-reference/grace-period.md" format="dita" scope="local">寬限期</a>。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>第 3<sup></sup></b> </p> </td> 
   <td colname="col2"> <p> <a href="../../introduction/cookies.md#section-7ff7d96d6e4141b08a84a75a63d7814c" format="dita" scope="local"> Experience Cloud ID (MID) </a> </p> </td> 
   <td colname="col3"> <p>訪客的瀏覽器接受第一方 Cookie.這會由 AMCV Cookie 設定。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>第 4<sup></sup></b> </p> </td> 
   <td colname="col2"> <p> <a href="https://docs.adobe.com/content/help/zh-Hant/id-service/using/reference/analytics-reference/analytics-ids.html" format="http" scope="external"> fid (H.25.3 或更新版本的後援 Cookie，或 JavaScript 適用的 AppMeasurement)</a> </p> </td> 
   <td colname="col3"> <p>瀏覽器不接受第三方 Cookie 且 Analytics 追蹤伺服器已設定為第三方追蹤伺服器。 </p> <p> <p>注意：如果您已在網站上實作 ID 服務，則舊版識別碼 <span class="codeph">fid</span> 並未使用。在此情況下就不需要 <span class="codeph">fid</span>，因為第一方 <a href="../../introduction/cookies.md" format="dita" scope="local"> AMCV Cookie</a> 已將其淘汰。保留它是為了支援舊版程式碼且供歷史記錄之用。 </p> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>第 5<sup></sup></b> </p> </td> 
   <td colname="col2"> <p> <a href="https://docs.adobe.com/content/help/zh-Hant/analytics/technotes/visitor-identification.html" format="http" scope="external"> IP 位址、使用者代理、閘道 IP 位址</a> </p> </td> 
   <td colname="col3"> <p>訪客的瀏覽器不接受 Cookie。 </p> </td> 
  </tr> 
 </tbody> 
</table>

