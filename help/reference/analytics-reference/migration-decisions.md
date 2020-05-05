---
description: 部署 Experience Cloud Identity 服務之前，請先瞭解如果使用不同方法或透過 JavaScript 檔案收集資料，此服務會對多網域的訪客追蹤功能造成哪些影響及潛在問題。
keywords: ID Service
seo-description: 部署 Experience Cloud Identity 服務之前，請先瞭解如果使用不同方法或透過 JavaScript 檔案收集資料，此服務會對多網域的訪客追蹤功能造成哪些影響及潛在問題。
seo-title: Experience Cloud Identity 服務移轉決策點
title: Experience Cloud Identity 服務移轉決策點
uuid: ee56b5de-fcf3-4cfb-9e53-762af7c4d2ff
translation-type: tm+mt
source-git-commit: d2bc0e7fedc4e48d51f5dad158f9f8bfcb0cb4f3

---


# Experience Cloud Identity 服務移轉決策點

部署 Experience Cloud Identity 服務之前，請先瞭解如果使用不同方法或透過 JavaScript 檔案收集資料，此服務會對多網域的訪客追蹤功能造成哪些影響及潛在問題。

請回答本節中的問題，有助於確定您所應執行的其他移轉步驟。

## 您有資料收集CNAME嗎？

許多客戶可從資料收集CNAME移轉出來，做為ID服務移轉的一部分。

<table id="table_13F7C1E3D64D4F86B0149C9D3B54AADD"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> 資料收集方法 </th> 
   <th colname="col2" class="entry"> 說明 </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p>使用CNAME </p> </td> 
   <td colname="col2"> <p>請參閱下一個問題，以決定您是否應從資料收集CNAME移轉走。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>沒有CNAME </p> </td> 
   <td colname="col2"> <p>請跳到<a href="../../reference/analytics-reference/migration-decisions.md#section-34dabde7780e4a339f134c0ca7768961" format="dita" scope="local">如果您沒有資料收集 CNAME，您的資料收集伺服器是否為 *.2o7.net 或 *.sc.omtrdc.net?</a>。 </p> </td> 
  </tr> 
 </tbody> 
</table>

## 如果您有資料收集CNAME，您有多個網域嗎？

如果您有多個網域將資料傳送至相同的報 *表套裝*，則建議您使用CNAME收集資料。 這有助於跨網域追蹤訪客。 如果您要在單一網域上收集資料，則維護資料收集CNAME沒有好處。

<table id="table_D132BCA243E54657AEC930559343FDD3"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> 從 </th> 
   <th colname="col2" class="entry"> 說明 </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p>多個網域 </p> </td> 
   <td colname="col2"> <p>如果您追蹤多個網域的訪客，而且您也有一個主要登入網站，可在客戶造訪其他網域之前加以識別，則您應繼續使用資料收集CNAME。 如需詳細說明，請參閱<a href="../../reference/analytics-reference/cname.md#concept-4df91f8a30ad4ec7a01eb943d579cc9d" format="dita" scope="local">資料收集 CNAME 和跨網域追蹤</a>。 </p> <p>請注意，您需要指定兩個額外的追蹤伺服器參數 <span class="codeph">visitor.marketingCloudServer</span> 和 <span class="codeph">visitor.marketingCloudServerSecure</span>，才能使用 ID 服務設定 CNAME。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>單一網域 </p> </td> 
   <td colname="col2"> <p>使用單一網域表示，如果您不想再管理資料收集CNAME，可以從中移轉。 不過，如果您的CNAME運作正常，則不需要變更。 </p> <p>如果您確實移除CNAME: </p> 
    <ul id="ul_12CDECEFC7BB41A18895B507CAA42315"> 
     <li id="li_32E2CD3E58454E20A642BADE507AE86E">確定新追蹤伺服器<a href="https://docs.adobe.com/content/help/en/analytics/technotes/rdc/regional-data-collection.html" format="https" scope="external">符合 RDC 標準</a>。 </li> 
     <li id="li_865BB6DAA3594EBBAB688E73C8343762">先從 CNAME 移至 RDC 追蹤伺服器，幾個月後再移轉至 <span class="keyword">Experience Cloud</span> ID 服務。 </li> 
     <li id="li_284A015177554C848C8648DC5BBAA365"> <i>請勿</i>使用 <span class="codeph"> *.2o7.net</span> 追蹤伺服器。 </li> 
     <li id="li_B1ABF03DC46C42059F61542CDE0FE5A1">聯絡<a href="https://helpx.adobe.com/tw/marketing-cloud/contact-support.html" format="https" scope="external">客戶服務</a>以設定訪客移轉。這可確保一致的訪客數。 </li> 
    </ul> </td> 
  </tr> 
 </tbody> 
</table>

## 您是否有多個 Analytics JavaScript 檔案，或您是否追蹤 Flash 應用程式或視訊?

如果您的網站上有多個會將資料傳送至&#x200B;*相同的報表套裝*&#x200B;的 Analytics JavaScript 檔案或 Flash 應用程式或視訊，則應設定寬限期，以便在您開始使用 [!DNL Experience Cloud] ID 服務時能繼續以 Analytics ID 識別訪客。

<table id="table_8A4EA063AF4345B69BC98537E2E702BA"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> 資料收集與 </th> 
   <th colname="col2" class="entry"> 必要動作 </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> 
    <ul id="ul_910DD99E074E49C6907F86426EFA5BF2"> 
     <li id="li_4366CC8EB7A54A959568E3761ABBBF23">多個Analytics Javascript檔案 </li> 
     <li id="li_B8A8132019EA48088E4F37E36F153D76">其他資料收集方法 </li> 
    </ul> </td> 
   <td colname="col2"> <p>您應設定訪客ID服務寬限期，以便將訪客ID服務推展至每個JavaScript檔案和其他資料收集程式庫。 See <a href="../../reference/analytics-reference/grace-period.md" format="dita" scope="local"> ID Service Grace Period</a>. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>單一Analytics JavaScript檔案 </p> </td> 
   <td colname="col2"> <p>您可以更新單一JavaScript檔案，以使用沒有寬限期的訪客ID服務。 </p> </td> 
  </tr> 
 </tbody> 
</table>

## 您使用不支援的資料收集方法嗎？

您可能需要更新追蹤連結或從Sliverlight移轉出去的方式。

<table id="table_A72AEB92F48345DD83F136B9989F4EF9"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> 資料收集方法 </th> 
   <th colname="col2" class="entry"> 必要動作 </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p>JavaScript和／或Flash </p> </td> 
   <td colname="col2"> <p>無. <span class="keyword">Experience Cloud</span> ID 服務支援這些資料收集方法。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>Silverlight </p> </td> 
   <td colname="col2"> <p>如果訪客可存取 Silverlight 內容及其他使用 <span class="keyword">Experience Cloud</span> ID 服務之網站上的區段，您需要從 Silverlight 移轉出來。ID服務不支援Silverlight。 </p> <p> 如果您追蹤以Silverlight為基礎的視訊播放器，廠商可能會提供您可改用的JavaScript API。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>硬式編碼影像標籤 </p> </td> 
   <td colname="col2"> <p>更新硬式編碼連結以使用JavaScript。 </p> </td> 
  </tr> 
 </tbody> 
</table>

