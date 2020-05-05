---
description: 傳回在 Experience Cloud Identity 服務實作前儲存於 s_vi Cookie 的舊有 Analytics ID (如果有的話)。如果之前未指派 Analytics ID 給訪客，則會傳回空字串。
keywords: ID Service
seo-description: 傳回在 Experience Cloud Identity 服務實作前儲存於 s_vi Cookie 的舊有 Analytics ID (如果有的話)。如果之前未指派 Analytics ID 給訪客，則會傳回空字串。
seo-title: getAnalyticsVisitorID
title: getAnalyticsVisitorID
uuid: 6bb8ddfc-9fc1-4105-b377-d9b4d247a0f8
translation-type: tm+mt
source-git-commit: d2bc0e7fedc4e48d51f5dad158f9f8bfcb0cb4f3

---


# getAnalyticsVisitorID{#getanalyticsvisitorid}

傳回在 Experience Cloud Identity 服務實作前儲存於 s_vi Cookie 的舊有 Analytics ID (如果有的話)。如果之前未指派 Analytics ID 給訪客，則會傳回空字串。

**語法** `var analyticsID = visitor.getAnalyticsVisitorID()`

通常，此函式會與需要讀取訪客ID的自訂解決方案搭配使用。 標準實作不會使用它。 `getAnalyticsVisitorID` 也會使用回呼函數讀取 [!DNL Analytics] ID，並將其帶入您的系統或應用程式。

**範例程式碼**

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
>如果您是 [!DNL Analytics] 客戶，請一併檢查 [!DNL Analytics] ID，並將其傳送至您的函數。例如，將隱藏表單元素中的訪客 ID 傳遞至使用資料插入 API 的伺服器端時，您會想要有兩個識別碼。在此情況下，您應該收集並傳回 [!DNL Experience Cloud] 與 [!DNL Analytics] 訪客 ID。請參閱 [getMarketingCloudVisitorID](../../library/get-set/getmcvid.md)。

**「aid」參數為舊有值 (Legacy Value)**

`aid` 參數會顯示在 2 組不同條件下的查詢字串中。

**案例 1**

發生下列情況時，您會在查詢字串中看到 `aid` 參數:

* 正確部署 [!DNL Experience Cloud] ID 服務。
* 造訪網站的使用者已在 [s_vi Cookie](https://docs.adobe.com/content/help/en/core-services/interface/ec-cookies/cookies-analytics.html#section-5d50a078de444d12b7d927d68ff3b679) 中儲存之前的 [!DNL Analytics] ID。

**案例 2**

如果貴組織在完全實作 ID 服務之前使用[寬限期](../../reference/analytics-reference/grace-period.md)，您便會在查詢字串中看到 `aid` 參數。如果使用者是第一次造訪網站，而您未使用寬限期，則訪客會得到 `mid` ([!DNL Experience Cloud] ID) 參數。

>[!MORELIKETHIS]
>
>* [Analytics Cookie](https://docs.adobe.com/content/help/en/core-services/interface/ec-cookies/cookies-privacy.html)

