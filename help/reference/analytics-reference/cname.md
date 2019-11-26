---
description: 'null'
keywords: order of operations;ID Service
seo-description: 'null'
seo-title: 資料收集 CNAME 和跨網域追蹤
title: 資料收集 CNAME 和跨網域追蹤
uuid: ba42c822-b677-4139-b1ed-4d98d3320fd0
translation-type: tm+mt
source-git-commit: 989b5f537848a7506a96e2eac17409f8b0307217

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

Analytics會使用第一方ID，除非已啟用第三方ID，否則瀏覽器會允許我們使用該ID。 第三方ID是客戶前取名的，因此客戶無法在Analytics中將資料與其他客戶結合。

## 舊版Analytics網域

在啟動Adobe訪客ID服務之前，許多客戶都使用原生分析網域來設定ID Cookie。 這些 `omtrdc.net`包 `2o7.net` 括或CNAME的網域。 `omtrdc.net`, `2o7.net`在某些情況下，會使用CNAME'd網域來儲存第三方Cookie。 以此方式設定的Cookie僅限於單一客戶，因此客戶無法將其資料與其他客戶的資料結合。 當客戶想要追蹤其擁有之網站(例如example.com、example.co.jp)上的使用者時，會使用第三方CNAMED的網域（有時稱為友好的第三方網域）。 此方法或使用CNAME支援好記的第三方網域已不建議使用，以提供更強穩且具隱私權的訪客ID服務。 客戶應在可行時，立即移至每個網域具有CNAME的訪客ID服務。

## 提供您自己的身分

如果客戶選擇透過Adobe的識別系統，並透過提供自訂訪客ID來建置自己 [的系統](https://docs.adobe.com/content/help/en/analytics/implementation/javascript-implementation/unique-visitors/visid-custom.md)。 如果您選擇此路由，有些事需要注意。

- 您需要實作選擇退出和適當的隱私權控制
- 該ID僅適用於Analytics
- 您必須負責保存該ID

## 資料收集CNAMES

Adobe仍建議搭配使用CNAME與訪客ID服務。 這可讓第一方訪客ID使用HTTP Cookies持續存在，讓Cookie更持久。

## OPTOUT

Adobe為客戶提供API，讓他們與我們的系統共用選擇退出訊號，讓客戶進而可讓使用者選擇追蹤。 我們提供客戶如何實施適當控制以支援使用者選擇的詳細指示；選擇 [退出API](https://docs.adobe.com/content/help/en/analytics/implementation/javascript-implementation/data-collection/opt-out.md) ，或在取得 [同意前防止Cookie觸發的](https://docs.adobe.com/content/help/en/id-service/using/implementation-guides/opt-in-service/optin-overview.md) 選項。

## 使用 Experience Cloud Identity 服務啟用 CNAME 支援 {#section-25d4feb686d944e3a877d7aad8dbdf9a}

資料收集伺服器CNAME支 [援可啟用設定CNAME](https://docs.adobe.com/content/help/en/core-services/interface/ec-cookies/cookies-first-party.md) ，並在Experience Cloud Identity service中設定 `visitor.marketingCloudServerSecure` 變數，以及在AppMeasurement中設定 `s.trackingServerSecure` 變數。
