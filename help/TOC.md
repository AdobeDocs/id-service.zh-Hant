---
cloud: platform-cloud
product: ID 服務
audience: 使用者
user-guide-title: Experience Cloud ID服務說明
user-guide-url: /content/help/en/id-service/using/home.html
translation-type: tm+mt
source-git-commit: 3e7b49564938527e1b6bca3a5fbaf9eb141d2e06

---


# Experience Cloud ID Service Help {#using}

+ [ID服務說明](home.md)
+ 概述 {#intro}
   + [概述](introduction/overview.md)
   + [關於ID服務](introduction/about-id-service.md)
   + [Cookie 和 ID 服務](introduction/cookies.md)
   + [ID服務要求和設定ID的方式](introduction/id-request.md)
   + [瞭解同步與匹配率](introduction/match-rates.md)
+ Implementation guides {#implementation-guides}
   + [實施指南](implementation-guides/implementation-guides.md)
   + [實施方法](implementation-guides/implementation-methods.md)
   + [使用 Launch 實作](implementation-guides/ecid-implement-with-launch.md)
   + [使用 DTM 的實作](implementation-guides/standard.md)
   + [實施Analytics](implementation-guides/setup-analytics.md)
   + [實施目標](implementation-guides/setup-target.md)
   + [實施Analytics和Audience Manager](implementation-guides/setup-aam-analytics.md)
   + [實施Analytics、Audience Manager和Target](implementation-guides/setup-aam-analytics-target.md)
   + [將 ID 服務用於 A4T 以及伺服器端的 Target 實作](implementation-guides/ecid-a4t-target.md)
   + [與ID服務直接整合](implementation-guides/direct-integration.md)
   + [直接整合的使用案例](implementation-guides/direct-integration-examples.md)
   + [測試並驗證ID服務](implementation-guides/test-verify.md)
   + Opt-in Documentation {#opt-in-service}
      + [選擇加入服務總覽](implementation-guides/opt-in-service/optin-overview.md)
      + [設定加入服務](implementation-guides/opt-in-service/getting-started.md)
      + [驗證選擇加入服務](implementation-guides/opt-in-service/testing-optin-and-iab-plugin.md)
      + [使用 Launch 設定選擇加入](implementation-guides/opt-in-service/launch.md)
      + [使用 DTM 設定選擇加入](implementation-guides/opt-in-service/optin-dtm.md)
      + [選擇加入使用案例](implementation-guides/opt-in-service/use-cases.md)
      + [選擇加入參考資料](implementation-guides/opt-in-service/api.md)
      + [(測試版)搭配使用選擇加入服務與IAB Framework](implementation-guides/opt-in-service/iab.md)
+ ID 服務 API {#id-service-api}
   + [ID服務API概述](library/library.md)
   + 設定 {#configurations}
      + [組態概觀](library/function-vars/function-vars.md)
      + [audienceManagerServer 及 audienceManagerServerSecure](library/function-vars/subdomain-config.md)
      + [cookieDomain](library/function-vars/cookiedomain.md)
      + [cookieLifetime](library/function-vars/cookielifetime.md)
      + [disableIdSyncs](library/function-vars/disableidsync.md)
      + [停用第三方通話](library/function-vars/disablethirdpartycalls.md)
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
      + [Analytics參考概述](reference/analytics-reference/analytics-reference.md)
      + [設定 Analytics 和 Experience Cloud ID](reference/analytics-reference/analytics-ids.md)
      + [Analytics ID 的作業順序](reference/analytics-reference/analytics-order-of-operations.md)
      + [ID服務移轉決策點](reference/analytics-reference/migration-decisions.md)
      + [ID服務移轉案例](reference/analytics-reference/migration-scenarios.md)
      + [分析和身分要求](reference/analytics-reference/legacy-analytics.md)
      + [資料收集 CNAME 和跨網域追蹤](reference/analytics-reference/cname.md)
      + [混用 JavaScript 的伺服器端實作](reference/analytics-reference/server-side.md)
      + [ID 服務寬限期](reference/analytics-reference/grace-period.md)
   + [內容保全政策和ID服務](reference/csp.md)
   + [ID服務中的COPPA支援](reference/coppa.md)
   + [ID服務中的CORS支援](reference/cors.md)
   + [客戶 ID 和驗證狀態](reference/authenticated-state.md)
   + [Safari ITP世界中的ECID程式庫方法](reference/ecid-library-methods.md)
   + [從 AMCV Cookie 或 ID 服務取得地區和使用者 ID](reference/regions.md)
   + [ID服務需求](reference/requirements.md)
   + [視訊心率和ID服務](reference/heartbeat.md)
   + [資料工作台和ID服務](reference/dwb.md)
+ 常見問題解答 {#faqs}
   + [常見問題概觀](faq-intro/faq-intro.md)
   + [ID 服務常見問題解答](faq-intro/faq.md)
   + [Analytics 與 ID 服務常見問題](faq-intro/analytics-faq.md)
   + [其他 Experience Cloud 解決方案的常見問題集](faq-intro/other-faq.md)
+ Release notes for ID Service {#release-notes}
   + [2019 年發行說明](release-notes/release-notes.md)
   + [2018 年發行說明](release-notes/notes-2018.md)
   + [2017 年發行說明](release-notes/notes-2017.md)
   + [2016 年發行說明](release-notes/notes-2016.md)
   + [2015 年發行說明](release-notes/notes-2015.md)
