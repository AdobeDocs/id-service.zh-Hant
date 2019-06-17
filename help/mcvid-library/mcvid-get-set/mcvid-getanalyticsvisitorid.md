---
description: 傳回在 Experience Cloud ID 服務實施前儲存在 s_vi cookie 中的舊有 Analytics ID (如果有的話)。如果之前未指派 Analytics ID 給訪客，則會傳回空字串。
keywords: ID 服務
seo-description: 傳回在 Experience Cloud ID 服務實施前儲存在 s_vi cookie 中的舊有 Analytics ID (如果有的話)。如果之前未指派 Analytics ID 給訪客，則會傳回空字串。
seo-title: getAnalyticsVisitorID
title: getAnalyticsVisitorID
uuid: 6bb8ddfc-9fc1-4105-b377-d9 b4 d247 a0 f8
translation-type: tm+mt
source-git-commit: bb687c1cd14aae7faef2565dcf9d041a1c06e3bd

---


# getAnalyticsVisitorID{#getanalyticsvisitorid}

傳回在 Experience Cloud ID 服務實施前儲存在 s_vi cookie 中的舊有 Analytics ID (如果有的話)。如果之前未指派 Analytics ID 給訪客，則會傳回空字串。

**語法** `var analyticsID = visitor.getAnalyticsVisitorID()`

通常，此函數會與需要讀取訪客 ID 的自訂解決方案搭配使用。標準實作不會使用此方法。`getAnalyticsVisitorID` 也會使用回呼函數讀取 [!DNL Analytics] ID，並將其帶入您的系統或應用程式。

**程式碼範例**

```js
//callback function 
var useAnalyticsVisitorID = function(id){ 
     //whatever your function does with the Experience Cloud ID 
}; 
 
//get Analytics ID and pass it to the function 
var analyticsID = visitor.getAnalyticsVisitorID(useAnalyticsVisitorID)
```

>[!TIP]
>
>如果您是 [!DNL Analytics] 客戶，請同時檢查並傳送 [!DNL Analytics] ID至您的函數。例如，將隱藏表單元素中的訪客 ID 傳遞至使用資料插入 API 的伺服器端時，您會想要有兩個識別碼。在此情況下，您應收集並傳回 [!DNL Experience Cloud][!DNL Analytics] 訪客ID。請參閱 [getMarketingCloudVisitorID](../../mcvid-library/mcvid-get-set/mcvid-getmcvid.md)。

**「aid」參數為舊有值 (Legacy Value)**

`aid` 參數會顯示在 2 組不同條件下的查詢字串中。

**案例 1**

發生下列情況時，您會在查詢字串中看到 `aid` 參數:

* [!DNL Experience Cloud] ID服務已正確部署。
* 造訪網站的使用者已在 [!DNL Analytics]s_vi Cookie[ 中儲存之前的 ](https://marketing.adobe.com/resources/help/en_US/whitepapers/cookies/?f=cookies_analytics.html) ID。

**案例 2**

您的組織 `aid` 在完整實作ID服務 [](../../mcvid-reference/mcvid-analytics-reference/mcvid-grace-period.md) 前，會在查詢字串中看到參數。如果使用者瀏覽您的網站，而您未使用寬限期，則訪客會取得 `mid` ( [!DNL Experience Cloud] ID)參數。

>[!MORE_贊_ this]
>
>* [Analytics Cookie](https://marketing.adobe.com/resources/help/en_US/whitepapers/cookies/cookies_analytics.html)

