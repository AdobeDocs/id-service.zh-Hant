---
description: 'null'
keywords: order of operations;ID Service
seo-description: 'null'
seo-title: 資料收集 CNAME 和跨網域追蹤
title: 資料收集 CNAME 和跨網域追蹤
uuid: ba42c822-b677-4139-b1ed-4d98d3320fd0
translation-type: tm+mt
source-git-commit: 588c4b29ebd3cccea4f2ab032f69a4b6c6e97f2a

---


# 資料收集與識別{#data-collection-and-identity}

在分析中，有三種方式可用來識別訪客。

- 使用訪 [客ID服務](https://docs.adobe.com/content/help/en/id-service/using/home.md)
- 使用舊 [版Analytics訪客ID](https://docs.adobe.com/content/help/en/analytics/implementation/javascript-implementation/unique-visitors/visid-overview.md)
- 提供其個人身分

## Using the Visitor ID Service{#using-the-visitor-id-service}

訪客ID服務是識別訪客的建議方式。 它基於兩個元件

- 第一方ID —— 可用於測量您自己網站訪客的第一方ID。 此ID會儲存在第一個參數ID中，同時儲存在用戶端Cookie和伺服器端Cookie中（使用CNAME）。
- 第三方ID（可選）-儲存在demdex.net上的單獨第三方ID，可用於測量跨多個網域（例如example.com和example.net）的訪客

Analytics一律會使用第一方ID，如果已啟用第三方ID並呈現，則每個網站上的第一方ID將相同。 不過，若因您的設定或瀏覽器封鎖第三方Cookie而停用第三方ID，則無法將兩個網站上的流量連結在一起。

## 舊版Analytics網域

在數年前訪客ID服務啟動之前，許多客戶使用原生分析網域來設定ID Cookie。 這些 `omtrdc.net`包 `2o7.net` 括或CNAME的網域。 `omtrdc.net`, `2o7.net` 且在某些情況下，會使用CNAME'd網域來儲存第三方Cookie。 以此方式設定的Cookie一律僅限於單一客戶，因此客戶無法跨公司合併其資料。 只有當客戶想要追蹤其擁有之網站的使用者(例如example.com、example.co.jp)時，才會使用第三方CNAMED的網域（有時稱為友好的第三方網域）。 此方法已遭淘汰，以提供更強穩和隱私權感知的訪客ID服務。 客戶應在可行時，立即移至每個網域具有CNAME的訪客ID服務。

## 提供您自己的身分

如果客戶選擇透過Adobe的識別系統，並透過提供自訂訪客ID來建置自己 [的系統](https://docs.adobe.com/content/help/en/analytics/implementation/javascript-implementation/unique-visitors/visid-custom.md)。 如果您選擇此路由，有些事需要注意。

- 您需要實作選擇退出和適當的隱私權控制
- 該ID僅適用於Analytics
- 您必須負責保存該ID

## 資料收集CNAMES

Adobe仍建議搭配使用CNAME與訪客ID服務。 這可讓第一方訪客ID使用HTTP Cookies持續存在，讓Cookie更持久。

## 退出

Adobe提供API來與我們的系統共用退出訊號，讓您為使用者提供退出追蹤的方式。 如需詳細指示，請 [參閱退出](https://docs.adobe.com/content/help/en/analytics/implementation/javascript-implementation/data-collection/opt-out.md)[和加入](https://docs.adobe.com/content/help/en/id-service/using/implementation-guides/opt-in-service/optin-overview.md)

## 使用 Experience Cloud Identity 服務啟用 CNAME 支援 {#section-25d4feb686d944e3a877d7aad8dbdf9a}

資料收集伺服器CNAME支 [援可啟用設定CNAME](https://docs.adobe.com/content/help/en/core-services/interface/ec-cookies/cookies-first-party.md) ，並在Experience Cloud Identity service中設定 `visitor.marketingCloudServerSecure` 變數，以及在AppMeasurement中設定 `s.trackingServerSecure` 變數。
