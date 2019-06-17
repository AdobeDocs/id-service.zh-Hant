---
cloud: experience-cloud
product: ID 服務
audience: 使用者
user-guide-title: ID服務說明
user-guide-url: /content/help/en/id-service/using/mcvid-home.html
translation-type: tm+mt
source-git-commit: c8020fc1cc5acd5fccb1e8a2e2787d95aa1294ab

---


# ID服務說明 {#using}

+ [Experience Cloud ID 服務](mcvid-home.md)
+ 概述 {#mcvid-introduction}
   + [概述](mcvid-introduction/mcvid-overview.md)
   + [關於ID服務](mcvid-introduction/mcvid-about-id-service.md)
   + [Cookie 和 Experience Cloud ID 服務](mcvid-introduction/mcvid-cookies.md)
   + [Experience Cloud ID服務請求的請求和設定ID](mcvid-introduction/mcvid-id-request.md)
   + [瞭解ID同步與匹配率](mcvid-introduction/mcvid-match-rates.md)
+ 實施指南 {#implementation-guides}
   + [實施指南](mcvid-implementation-guides/mcvid-implementation-guides.md)
   + [實施方法](mcvid-implementation-guides/mcvid-implementation-methods.md)
   + [使用 Launch 實作](mcvid-implementation-guides/ecid-implement-with-launch.md)
   + [使用動態標籤管理進行實施](mcvid-implementation-guides/mcvid-standard.md)
   + [實施適用於 Analytics 的 Experience Cloud ID 服務](mcvid-implementation-guides/mcvid-setup-analytics.md)
   + [實施適用於 Target 的 Experience Cloud ID 服務](mcvid-implementation-guides/mcvid-setup-target.md)
   + [實施適用於 Analytics 和 Audience Manager 的 Experience Cloud ID 服務](mcvid-implementation-guides/mcvid-setup-aam-analytics.md)
   + [實施適用於 Analytics、Audience Manager 和 Target 的 Experience Cloud ID 服務](mcvid-implementation-guides/mcvid-setup-aam-analytics-target.md)
   + [將 Experience Cloud ID 服務用於 A4T 以及伺服器端的 Target 實作](mcvid-implementation-guides/ecid-a4t-target.md)
   + [與 Experience Cloud ID 服務直接整合](mcvid-implementation-guides/mcvid-direct-integration.md)
   + [直接整合的使用案例](mcvid-implementation-guides/mcvid-direct-integration-examples.md)
   + [測試並驗證Experience Cloud ID服務](mcvid-implementation-guides/mcvid-test-verify.md)
   + 選擇加入文件 {#opt-in-service}
      + [選擇加入服務總覽](mcvid-implementation-guides/opt-in-service/mcvid-optin-overview.md)
      + [設定加入服務](mcvid-implementation-guides/opt-in-service/getting-started.md)
      + [驗證選擇加入服務](mcvid-implementation-guides/opt-in-service/testing-optin-and-iab-plugin.md)
      + [使用 Launch 設定選擇加入](mcvid-implementation-guides/opt-in-service/launch.md)
      + [使用 DTM 設定選擇加入](mcvid-implementation-guides/opt-in-service/optin-dtm.md)
      + [選擇加入使用案例](mcvid-implementation-guides/opt-in-service/use-cases.md)
      + [選擇加入參考資料](mcvid-implementation-guides/opt-in-service/api.md)
      + [(測試版)搭配使用選擇加入服務與IAB Framework](mcvid-implementation-guides/opt-in-service/iab.md)
+ ID 服務 API {#id-service-api}
   + 設定 {#configurations}
      + [組態概觀](mcvid-library/mcvid-function-vars/mcvid-function-vars.md)
      + [audienceManagerServer 及 audienceManagerServerSecure](mcvid-library/mcvid-function-vars/mcvid-subdomain-config.md)
      + [cookieDomain](mcvid-library/mcvid-function-vars/mcvid-cookiedomain.md)
      + [cookieLifetime](mcvid-library/mcvid-function-vars/mcvid-cookielifetime.md)
      + [disableIdSyncs](mcvid-library/mcvid-function-vars/mcvid-disableidsync.md)
      + [停用第三方通話](mcvid-library/mcvid-function-vars/mcvid-disablethirdpartycalls.md)
      + [disableThirdPartyCookies](mcvid-library/mcvid-function-vars/mcvid-disable-cookies.md)
      + [idSyncAttachIframeOnWindowLoad](mcvid-library/mcvid-function-vars/mcvid-idsyncattachiframeonwindowload.md)
      + [idSyncContainerID](mcvid-library/mcvid-function-vars/mcvid-idsyncontainerid.md)
      + [idSyncSSLUseAkamai](mcvid-library/mcvid-function-vars/mcvid-idsyncssluseakamai.md)
      + [isCoopSafe](mcvid-library/mcvid-function-vars/mcvid-coopsafe.md)
      + [loadTimeout](mcvid-library/mcvid-function-vars/mcvid-loadtimeout.md)
      + [overwriteCrossDomainMCIDAndAID](mcvid-library/mcvid-function-vars/mcvid-overwrite-visitor-id.md)
      + [resetBeforeVersion](mcvid-library/mcvid-function-vars/mcvid-resetbeforeversion.md)
      + [sdidParamExpiry](mcvid-library/mcvid-function-vars/mcvid-sdidparamexpiry.md)
      + [secureCookie](mcvid-library/mcvid-function-vars/mcvid-securecookie.md)
      + [useCORSOnly](mcvid-library/mcvid-function-vars/mcvid-use-cors-only.md)
      + [whitelistParentDomain 及 whitelistIframeDomains](mcvid-library/mcvid-function-vars/mcvid-whitelistdomain.md)
   + 方法 {#methods}
      + [方法](mcvid-library/mcvid-get-set/mcvid-get-set.md)
      + [appendSupplementalDataIDTo](mcvid-library/mcvid-get-set/mcvid-appendsupplementaldataidto.md)
      + [appendVisitorIDsTo (跨網域追蹤)](mcvid-library/mcvid-get-set/mcvid-appendvisitorid.md)
      + [callTimeOut 方法](mcvid-library/mcvid-get-set/mcvid-timeout-functions.md)
      + [依 URL 或資料來源執行 ID 同步作業](mcvid-library/mcvid-get-set/mcvid-idsync.md)
      + [getInstance](mcvid-library/mcvid-get-set/mcvid-getinstance.md)
      + [getAnalyticsVisitorID](mcvid-library/mcvid-get-set/mcvid-getanalyticsvisitorid.md)
      + [getCustomerIDs](mcvid-library/mcvid-get-set/mcvid-getcustomerids.md)
      + [setCustomerIDs](mcvid-library/mcvid-get-set/mcvid-setcustomerids.md)
      + [getMarketingCloudVisitorID](mcvid-library/mcvid-get-set/mcvid-getmcvid.md)
      + [getLocationHint](mcvid-library/mcvid-get-set/mcvid-getlocationhint.md)
      + [getVisitorValues](mcvid-library/mcvid-get-set/mcvid-getvisitorvalues.md)
      + [isClientSideMarketingCloudVisitorID](mcvid-library/mcvid-get-set/mcvid-client-side-id.md)
      + [resetState](mcvid-library/mcvid-get-set/mcvid-resetstate.md)
+ 參考 {#reference}
   + Analytics 參考 {#analytics-reference}
      + [Analytics參考概述](mcvid-reference/mcvid-analytics-reference/mcvid-analytics-reference.md)
      + [設定 Analytics 和 Experience Cloud ID](mcvid-reference/mcvid-analytics-reference/mcvid-analytics-ids.md)
      + [Analytics ID 的作業順序](mcvid-reference/mcvid-analytics-reference/mcvid-analytics-order-of-operations.md)
      + [Experience Cloud ID 服務移轉決策點](mcvid-reference/mcvid-analytics-reference/mcvid-migration-decisions.md)
      + [Experience Cloud ID 服務移轉案例](mcvid-reference/mcvid-analytics-reference/mcvid-migration-scenarios.md)
      + [Analytics 與 Experience Cloud ID 請求](mcvid-reference/mcvid-analytics-reference/mcvid-legacy-analytics.md)
      + [資料收集 CNAME 和跨網域追蹤](mcvid-reference/mcvid-analytics-reference/mcvid-cname.md)
      + [混用 JavaScript 的伺服器端實作](mcvid-reference/mcvid-analytics-reference/mcvid-server-side.md)
      + [ID 服務寬限期](mcvid-reference/mcvid-analytics-reference/mcvid-grace-period.md)
   + [內容安全性原則及 Experience Cloud ID 服務](mcvid-reference/mcvid-csp.md)
   + [Experience Cloud ID 服務的 COPPA 支援](mcvid-reference/mcvid-coppa.md)
   + [Experience Cloud ID 服務的 CORS 支援](mcvid-reference/mcvid-cors.md)
   + [客戶 ID 和驗證狀態](mcvid-reference/mcvid-authenticated-state.md)
   + [從 AMCV Cookie 或 ID 服務取得地區和使用者 ID](mcvid-reference/mcvid-regions.md)
   + [Experience Cloud ID 服務規定](mcvid-reference/mcvid-requirements.md)
   + [影片心率和 Experience Cloud ID 服務](mcvid-reference/mcvid-heartbeat.md)
   + [Data Workbench 與 Experience Cloud ID 服務](mcvid-reference/mcvid-dwb.md)
+ 常見問題解答 {#faqs}
   + [常見問題概觀](mcvid-faq-intro/mcvid-faq-intro.md)
   + [ID 服務常見問題解答](mcvid-faq-intro/mcvid-faq.md)
   + [Analytics 與 ID 服務常見問題](mcvid-faq-intro/mcvid-analytics-faq.md)
   + [其他 Experience Cloud 解決方案的常見問題集](mcvid-faq-intro/mcvid-other-faq.md)
+ ID服務的發行說明 {#release-notes}
   + [2019 年發行說明](mcvid-release-notes/mcvid-release-notes.md)
   + [2018 年發行說明](mcvid-release-notes/mcvid-notes-2018.md)
   + [2017 年發行說明](mcvid-release-notes/mcvid-notes-2017.md)
   + [2016 年發行說明](mcvid-release-notes/mcvid-notes-2016.md)
   + [2015 年發行說明](mcvid-release-notes/mcvid-notes-2015.md)
