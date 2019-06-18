---
description: 'Experience Cloud ID 服務提供永久性的通用 ID，可識別 Experience Cloud 所有解決方案中的訪客。 '
keywords: ID 服務
seo-description: Adobe Experience Cloud ID服務提供通用的永久性ID，可識別Experience Cloud所有解決方案中的訪客。它可取代 Analytics、Audience Manager、Target 等服務及其他 Experience Cloud 解決方案或功能的 ID 產生碼。
seo-title: Experience Cloud ID 服務
title: Experience Cloud ID 服務
uuid: b68194b-e549-4f6 f-bfaf-7744926eaaac
translation-type: tm+mt
source-git-commit: cce8f5559baa0598fedaccf2fece6ec90cb641b7

---


# Experience Cloud ID 服務 {#experience-cloud-id-service}

Experience Cloud ID 服務 (以下簡稱為「ID 服務」) 提供永久性的通用 ID，可識別 Experience Cloud 中所有解決方案的訪客。它可取代 Analytics、Audience Manager、Target 等服務及其他 Experience Cloud 解決方案或功能的 ID 產生碼。

<table id="table_5E612F746A704FE095B809A013EE977F" class="simpletable"> 
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <b>快速入門</b> </p> <p> 
     <ul id="ul_D5EC6A54A03F4AB595B588116A7C1296"> 
      <li id="li_845F6DE25A1241439BCDCBC00459D7EB"> <a href="mcvid-introduction/mcvid-overview.md" format="dita" scope="local"> 概述 </a> </li> 
      <li id="li_47F399E1D4AF4F08BD647DF01A423BA7"> <a href="mcvid-reference/mcvid-requirements.md" format="dita" scope="local"> Experience Cloud ID 服務規定 </a> </li> 
      <li id="li_CBEEE79B45644F28A52B58DDF23DAD4F"> <a href="mcvid-implementation-guides/mcvid-standard.md#concept-89cd0199a9634fc48644f2d61e3d2445" format="dita" scope="local"> 透過 DTM 實現的標準實施 </a> </li> 
     </ul> </p> <p><b>Experience Cloud ID Javascript 資料庫</b> </p> <p>Experience Cloud ID 服務的 JavaScript 位於: <a href="https://github.com/Adobe-Marketing-Cloud/id-service/releases" format="https" scope="external">https://github.com/Adobe-Marketing-Cloud/id-service/releases</a> </p> <p> <b>全新或精選項目</b> </p> <p> 
     <ul id="ul_B0A25B6827734D55BB1E20D12334AC21"> 
      <li id="li_A66924F4948F4A5ABA545A89A28A6F6A"><a href="mcvid-implementation-guides/opt-in-service/mcvid-optin-overview.md#concept-f9b5db0d27a245fbadd3e19162319360" format="dita" scope="local"> 選擇加入服務</a> </li> 
      <li id="li_92D49CB788AD478EA74BCF5328CB9A14"> <a href="mcvid-library/mcvid-get-set/mcvid-getvisitorvalues.md#reference-b8c9e17c170c4291829a792df46ce279" format="dita" scope="local"> getVisitorValues </a> </li> 
      <li id="li_9E512C6DD15C46C3ABD06ACD60D97E4A"> <a href="mcvid-faq-intro/ecid-faq-intro.md" format="dita" scope="local"> 常見問題解答 </a> </li> 
      <li id="li_B28082F3D075413D89E5AFB718657E17"> <a href="mcvid-library/mcvid-function-vars/mcvid-coopsafe.md#reference-7fbed36f38a048d1a5883c53d430ddf4" format="dita" scope="local"> isCoopSafe </a> </li> 
      <li id="li_7744A4898EA542B9BF009D2066810050"> <a href="mcvid-library/mcvid-function-vars/mcvid-idsyncontainerid.md#reference-5cfbed2240fa4def90f535f017a36015" format="dita" scope="local"> idSyncContainerID </a> </li> 
     </ul> </p> 
    <draft-comment> 
     <p> <b>公告:</b> </p> 
     <p> <p>重要：Internet Explorer6、和8的ID服務支援已過時，未來將會停止發行。 </p> </p> 
    </draft-comment> </td> 
   <td colname="col2"> <p> <b>發行說明</b> </p> <p><b>2019年</b> 月12日發行的版本包含 <a href="mcvid-implementation-guides/opt-in-service/mcvid-optin-overview.md#concept-f9b5db0d27a245fbadd3e19162319360" format="dita" scope="local"> 可用來識別您在瀏覽您的網站時，是否可以在使用者裝置或瀏覽器上放置Cookie的選擇加入服務</a> 。 </p> <p>2018 年 1 月 18 日發行的版本包含 3.0.0 JavaScript 更新以及 API 方法的更新。請參閱<a href="mcvid-library/mcvid-function-vars/mcvid-disableidsync.md#reference-589d6b489ac64eddb5a7ff758945e414" format="dita" scope="local"> disableIDSyncCS</a> 和 <a href="mcvid-library/mcvid-function-vars/mcvid-disable-cookies.md#reference-2dd2d60d12f34f0b98bbb5606b3734cc" format="dita" scope="local"> disableThirdPartyCookie</a>。 </p> 
    <draft-comment> 
     <p>2017年10月版本不包含ID服務的任何程式碼變更或更新。ID服務程式碼在v2.5時維持不變。 </p> 
    </draft-comment> 
    <draft-comment> 
     <p> 2017年月發行版本將ID服務程式碼增加至v2.5。 </p> 
    </draft-comment> <p> 
     <ul id="ul_4F06F170F214492780C7D25A069F799F"> 
      <li id="li_45A7CD556FE44F4DAB035C736A058F36"> 請參閱最新的 <a href="https://marketing.adobe.com/resources/help/en_US/whatsnew/" format="https" scope="external">Experience Cloud 發行說明</a>，瞭解全新功能和修正內容。 </li> 
      <li id="li_10CC4FBFEFC947CA9AD15F52D9715257">請參閱<a href="https://marketing-stage.adobe.com/resources/help/en_US/whatsnew/c_legacy_releases.html" format="html" scope="external">之前的發行說明</a>，瞭解以往的發行。 </li> 
     </ul> </p> <p> <b>Experience Cloud 資源</b> </p> <p> 
     <ul id="ul_E30EC96BDC624B5591F0470D430B7F41"> 
      <li id="li_F3A5CCFAE0F247CEB41A03CA8E03106B"> <a href="http://www.adobe.com/privacy.html" format="http" scope="external"> Adobe 隱私中心</a> </li> 
      <li id="li_A54C1EB170EA4B8FA6A81B90AB0C39DD"> <a href="http://www.adobe.com/marketing-cloud.html" scope="external" format="http"> Adobe Experience Cloud</a> </li> 
      <li id="li_1938F7044F544481A6CC0F45CC22B80A"> <a href="http://helpx.adobe.com/learning.html?promoid=KAUDK" scope="external" format="http"> Adobe 培訓和教學課程</a> </li> 
      <li id="li_C71459E0D1464C05B8B9387C43541F17"> <a href="https://marketing.adobe.com/resources/help/en_US/home/index.html" scope="external" format="https"> 產品文件首頁</a> </li> 
     </ul> </p> </td> 
  </tr> 
 </tbody> 
</table>

