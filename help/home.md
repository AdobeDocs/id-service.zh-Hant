---
description: Experience Cloud Identity Service 可為 Experience Cloud 應用程式和服務啟用共同識別架構。它透過為網站訪客指派唯一、持續存在的 ID 來運作，稱為 Experience Cloud ID (ECID)。
keywords: ID 服務；Identity Service；Experience Cloud Identity Service
title: Experience Cloud Identity Service
exl-id: fe1368db-06ca-4c79-b655-b7064e316d74
source-git-commit: f7c25f5ebd0690c56c081422949eb34f1f277ae1
workflow-type: tm+mt
source-wordcount: '355'
ht-degree: 100%

---

# Adobe Experience Cloud Identity Service {#experience-cloud-id-service}

Experience Cloud Identity Service 可為 Experience Cloud 應用程式和服務啟用共同識別架構。它透過為網站訪客指派唯一、持續存在的 ID 來運作，稱為 Experience Cloud ID (ECID)。

## 了解身分的主要實體

若要更進一步了解 Adobe 如何有助於唯一地識別訪客並解析身分資訊，請閱讀以下細目：

* **Experience Cloud Identity Service**：Experience Cloud Identity Service **負責設定 Experience Cloud ID (ECID)**。 如需詳細資訊，請閱讀 [Experience Cloud Identity Service 概觀](./introduction/overview.md)。
* **Experience Cloud ID (ECID)**：ECID 是跨 Adobe Experience Platform 和 Adobe Experience Cloud 應用程式使用的共用身分命名空間，用於識別人員和裝置。如需有關 ECID 的詳細資訊，請閱讀 [ECID 概觀](https://experienceleague.adobe.com/docs/experience-platform/identity/ecid.html?lang=zh-Hant)。
* **Experience Platform Identity Service**：Experience Platform Identity Service 透過跨裝置和系統橋接身分，為您提供客戶及其行為的全面視野。如需詳細資訊，請閱讀 [Experience Platform Identity Service 概觀](https://experienceleague.adobe.com/docs/experience-platform/identity/home.html?lang=zh-Hant)。

<!-- The Adobe Experience Cloud Identity Service provides a universal, persistent ID that identifies your visitors across all the solutions in the Experience Cloud. It can replace ID generation code for Experience Cloud solutions and services. -->

<table id="table_5E612F746A704FE095B809A013EE977F" class="simpletable"> 
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <b>快速入門</b> </p> <p> 
     <ul id="ul_D5EC6A54A03F4AB595B588116A7C1296"> 
      <li id="li_845F6DE25A1241439BCDCBC00459D7EB"> <a href="introduction/overview.md" format="dita" scope="local">總覽</a> </li> 
      <li id="li_47F399E1D4AF4F08BD647DF01A423BA7"> <a href="reference/requirements.md" format="dita" scope="local"> Experience Cloud Identity Service 的需求 </a> </li> 
      <li id="li_CBEEE79B45644F28A52B58DDF23DAD4F"> <a href="https://experienceleague.adobe.com/docs/experience-platform/tags/home.html?lang=zh-Hant&lank=zh-Hant" format="html" scope="external">包含 Platform 標籤的標準實作</a> </li> 
     </ul> </p> <p><b>Experience Cloud ID JavaScript 程式庫</b> </p> <p>Experience Cloud Identity Service 的 JavaScript 位於：<a href="https://github.com/Adobe-Marketing-Cloud/id-service/releases" format="https" scope="external">https://github.com/Adobe-Marketing-Cloud/id-service/releases</a> </p> <p> <b>全新或精選項目</b> </p> <p> 
     <ul id="ul_B0A25B6827734D55BB1E20D12334AC21"> 
      <li id="li_A66924F4948F4A5ABA545A89A28A6F6A"><a href="implementation-guides/opt-in-service/optin-overview.md#concept-f9b5db0d27a245fbadd3e19162319360" format="dita" scope="local">選擇加入服務</a> </li> 
      <li id="li_92D49CB788AD478EA74BCF5328CB9A14"> <a href="library/get-set/getvisitorvalues.md#reference-b8c9e17c170c4291829a792df46ce279" format="dita" scope="local"> getVisitorValues </a> </li> 
      <li id="li_9E512C6DD15C46C3ABD06ACD60D97E4A"> <a href="faq-intro/faq-intro.md" format="dita" scope="local"> 常見問題集 </a> </li> 
      <li id="li_7744A4898EA542B9BF009D2066810050"> <a href="library/function-vars/idsyncontainerid.md#reference-5cfbed2240fa4def90f535f017a36015" format="dita" scope="local"> idSyncContainerID </a> </li> 
     </ul> </p> 
     <!-- 
     <p> <b>Announcements:</b> </p> 
     <p> <p>Important:  ID service support for Internet Explorer 6, 7, and 8 is deprecated and will be discontinued in a future release. </p> </p> 
     --> </td> 
   <td colname="col2"> <p> <b>版本注意事項</b> </p> <p><b>4.4 版</b> 2019 年 7 月 17 日發行版本包含 <a href="reference/hashing-support.md" format="dita" scope="local">SHA-256 雜湊演算法</a>支援，可讓您傳入客戶 ID 或電子郵件地址，然後傳出雜湊 ID。</p><p><b>4.0 版</b> 2019 年 2 月 12 日發行版本包含<a href="implementation-guides/opt-in-service/optin-overview.md#concept-f9b5db0d27a245fbadd3e19162319360" format="dita" scope="local">選擇加入服務</a>，用於識別您是否可在用戶造訪您的網站時於其裝置上或瀏覽器上放置 Cookie。 </p> <p> 
     <ul id="ul_4F06F170F214492780C7D25A069F799F"> 
      <li id="li_45A7CD556FE44F4DAB035C736A058F36"> 請參閱最新的 <a href="https://experienceleague.adobe.com/docs/release-notes/experience-cloud/current.html?lang=zh-Hant" format="https" scope="external">Experience Cloud 版本注意事項</a>，了解全新功能和修正內容。 </li> 
      <li id="li_10CC4FBFEFC947CA9AD15F52D9715257">請參閱<a href="https://experienceleague.adobe.com/docs/release-notes/experience-cloud/current.html?lang=zh-Hant" format="html" scope="external">之前的版本注意事項</a>一節，了解較舊的版本。 </li> 
     </ul> </p> <p> <b>Experience Cloud 資源</b> </p> <p> 
     <ul id="ul_E30EC96BDC624B5591F0470D430B7F41"> 
      <li id="li_F3A5CCFAE0F247CEB41A03CA8E03106B"> <a href="https://www.adobe.com/tw/privacy.html" format="http" scope="external"> Adobe 隱私中心</a> </li> 
      <li id="li_A54C1EB170EA4B8FA6A81B90AB0C39DD"> <a href="https://experienceleague.adobe.com/docs/home.html?lang=zh-Hant" scope="external" format="http"> Adobe Experience Cloud</a> </li> 
      <li id="li_1938F7044F544481A6CC0F45CC22B80A"> <a href="http://helpx.adobe.com/tw/learning.html?promoid=KAUDK" scope="external" format="http"> Adobe 培訓和教學課程</a> </li> 
      <li id="li_C71459E0D1464C05B8B9387C43541F17"> <a href="https://helpx.adobe.com/tw/support/experience-cloud.html" scope="external" format="https"> 產品文件首頁</a> </li> 
     </ul> </p> </td> 
  </tr> 
 </tbody> 
</table>
