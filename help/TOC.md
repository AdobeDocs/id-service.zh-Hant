---
cloud: platform-cloud
product: ID 服務
audience: 終端使用者
user-guide-title: Experience Cloud Identity 服務說明
user-guide-url: /content/help/zh-Hant/id-service/using/home.html
translation-type: tm+mt
source-git-commit: 11578e184a86625a246fee84c65fcdee1a086c45

---


# Experience Cloud Identity 服務說明 {#using}

+ [ID 服務說明](home.md)
+ 概述 {#intro}
   + [概述](introduction/overview.md)
   + [關於 ID 服務](introduction/about-id-service.md)
   + [Cookie 與 ID 服務](introduction/cookies.md)
   + [ ID 服務如何要求與設定 ID](introduction/id-request.md)
   + [了解同步和匹配率](introduction/match-rates.md)
+ 實作指南 {#implementation-guides}
   + [實作指南](implementation-guides/implementation-guides.md)
   + [實作方式](implementation-guides/implementation-methods.md)
   + [使用 Experience Platform Launch 實作](implementation-guides/ecid-implement-with-launch.md)
   + [使用 DTM 實作](implementation-guides/standard.md)
   + [實作 Analytics](implementation-guides/setup-analytics.md)
   + [實作 Target](implementation-guides/setup-target.md)
   + [實作 Analytics 與 Audience Manager](implementation-guides/setup-aam-analytics.md)
   + [實作 Analytics、Audience Manager 及 Target](implementation-guides/setup-aam-analytics-target.md)
   + [將 ID 服務用於 A4T 以及伺服器端的 Target 實作](implementation-guides/ecid-a4t-target.md)
   + [與 ID 服務直接整合](implementation-guides/direct-integration.md)
   + [直接整合的使用案例](implementation-guides/direct-integration-examples.md)
   + [測試及驗證 ID 服務](implementation-guides/test-verify.md)
   + 選擇加入服務文件 {#opt-in-service}
      + [選擇加入服務概述](implementation-guides/opt-in-service/optin-overview.md)
      + [設定選擇加入服務](implementation-guides/opt-in-service/getting-started.md)
      + [驗證選擇加入服務](implementation-guides/opt-in-service/testing-optin-and-iab-plugin.md)
      + [使用 Experience Platform Launch 設定選擇加入](implementation-guides/opt-in-service/launch.md)
      + [使用 DTM 設定選擇加入](implementation-guides/opt-in-service/optin-dtm.md)
      + [選擇加入使用案例](implementation-guides/opt-in-service/use-cases.md)
      + [選擇加入參考資料](implementation-guides/opt-in-service/api.md)
      + [(測試版) 搭配 IAB 架構使用選擇加入服務](implementation-guides/opt-in-service/iab.md)
+ ID 服務 API {#id-service-api}
   + [ID 服務 API 概述](library/library.md)
   + 設定 {#configurations}
      + [設定概述](library/function-vars/function-vars.md)
      + [audienceManagerServer 及 audienceManagerServerSecure](library/function-vars/subdomain-config.md)
      + [cookieDomain](library/function-vars/cookiedomain.md)
      + [cookieLifetime](library/function-vars/cookielifetime.md)
      + [disableIdSyncs](library/function-vars/disableidsync.md)
      + [disableThirdPartyCalls](library/function-vars/disablethirdpartycalls.md)
      + [disableThirdPartyCookies](library/function-vars/disable-cookies.md)
      + [idSyncAttachIframeOnWindowLoad](library/function-vars/idsyncattachiframeonwindowload.md)
      + [idSyncContainerID](library/function-vars/idsyncontainerid.md)
      + [idSyncSSLUseAkamai](library/function-vars/idsyncssluseakamai.md)
      + [isCoopSafe](library/function-vars/coopsafe.md)
      + [loadTimeout](library/function-vars/loadtimeout.md)
      + [overwriteCrossDomainMCIDAndAID](library/function-vars/overwrite-visitor-id.md)
      + [resetBeforeVersion](library/function-vars/resetbeforeversion.md)
      + [sdidParamExpiry](library/function-vars/sdidparamexpiry.md)
      + [secureCookie](library/function-vars/securecookie.md)
      + [useCORSOnly](library/function-vars/use-cors-only.md)
      + [whitelistParentDomain 及 whitelistIframeDomains](library/function-vars/whitelistdomain.md)
   + 方法 {#methods}
      + [方法](library/get-set/get-set.md)
      + [appendSupplementalDataIDTo](library/get-set/appendsupplementaldataidto.md)
      + [appendVisitorIDsTo (跨網域追蹤)](library/get-set/appendvisitorid.md)
      + [callTimeOut 方法](library/get-set/timeout-functions.md)
      + [依 URL 或資料來源執行 ID 同步作業](library/get-set/idsync.md)
      + [getInstance](library/get-set/getinstance.md)
      + [getAnalyticsVisitorID](library/get-set/getanalyticsvisitorid.md)
      + [getCustomerIDs](library/get-set/getcustomerids.md)
      + [setCustomerIDs](library/get-set/setcustomerids.md)
      + [getMarketingCloudVisitorID](library/get-set/getmcvid.md)
      + [getLocationHint](library/get-set/getlocationhint.md)
      + [getVisitorValues](library/get-set/getvisitorvalues.md)
      + [isClientSideMarketingCloudVisitorID](library/get-set/client-side-id.md)
      + [resetState](library/get-set/resetstate.md)
+ 參考 {#reference}
   + [參考概述](reference/reference.md)
   + Analytics 參考 {#analytics-reference}
      + [Analytics 參考概述](reference/analytics-reference/analytics-reference.md)
      + [設定 Analytics 和 Experience Cloud ID](reference/analytics-reference/analytics-ids.md)
      + [Analytics ID 的作業順序](reference/analytics-reference/analytics-order-of-operations.md)
      + [ID 服務移轉決策點](reference/analytics-reference/migration-decisions.md)
      + [ID 服務移轉案例](reference/analytics-reference/migration-scenarios.md)
      + [Analytics 和 Identity 要求](reference/analytics-reference/legacy-analytics.md)
      + [資料收集 CNAME 和跨網域追蹤](reference/analytics-reference/cname.md)
      + [混用 JavaScript 的伺服器端實作](reference/analytics-reference/server-side.md)
      + [ID 服務寬限期](reference/analytics-reference/grace-period.md)
   + [內容安全性原則及 ID 服務](reference/csp.md)
   + [ID 服務的 COPPA 支援](reference/coppa.md)
   + [ID 服務的 CORS 支援](reference/cors.md)
   + [客戶 ID 和驗證狀態](reference/authenticated-state.md)
   + [Safari ITP 領域的 ECID 程式庫方法](reference/ecid-library-methods.md)
   + [從 AMCV Cookie 或 ID 服務取得地區和使用者 ID](reference/regions.md)
   + [ID 服務規定](reference/requirements.md)
   + [影片心率和 ID 服務](reference/heartbeat.md)
   + [Data Workbench 與 ID 服務](reference/dwb.md)
   + [setCustomerIDs 的 SHA256 雜湊支援](reference/hashing-support.md)
+ 常見問題集 {#faqs}
   + [常見問題集概述](faq-intro/faq-intro.md)
   + [ID 服務常見問題集](faq-intro/faq.md)
   + [Analytics 與 ID 服務常見問題集](faq-intro/analytics-faq.md)
   + [其他 Experience Cloud 解決方案的常見問題集](faq-intro/other-faq.md)
+ ID 服務發行說明 {#release-notes}
   + [2019 年發行說明](release-notes/release-notes.md)
   + [2018 年發行說明](release-notes/notes-2018.md)
   + [2017 年發行說明](release-notes/notes-2017.md)
   + [2016 年發行說明](release-notes/notes-2016.md)
   + [2015 年發行說明](release-notes/notes-2015.md)
