---
description: 使用這些設定，可將呼叫訪客ID服務使用的預設網域名稱變更為您擁有的子網域名稱。
keywords: 訪客 ID 服務
title: audienceManagerServer 及 audienceManagerServerSecure
exl-id: b740eb5c-ac4e-46f4-ba7c-1080d8d9292d
TQID: https://experienceleague.adobe.com/a5KVErDX4putY8d9vGf-uAwswNzE0Maf-JEyfmQxhbg
product_v2: id: e1971122-7081-4556-9222-8a31bd71800c
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554id: c66ffd68-0f65-42bb-aa23-b4020f12e0bdid: f8a45b24-4be7-4f1b-909b-60d06b483a20id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
source-git-commit: 09ee359440c122702a6ce83708c98af3862c9cc9
workflow-type: tm+mt
source-wordcount: 234
ht-degree: 44%

---

# audienceManagerServer 及 audienceManagerServerSecure{#audiencemanagerserver-and-audiencemanagerserversecure}

使用這些設定，可將呼叫訪客ID服務使用的預設網域名稱變更為您擁有的子網域名稱。

**語法:**

* `audienceManagerServer: " *`您的子網域名稱`*.demdex.net"`
* `audienceManagerServerSecure: " *`您的子網域名稱`*.demdex.net"`

**用途**

訪客ID服務通常會在`dpm.demdex.net`呼叫Adobe。 有時候，您會覺得此目的地看起來太普遍或太像「第三方」而不想進行呼叫。 若要讓訪客ID服務呼叫看起來更像第一方呼叫，請使用這些設定將您的Audience Manager子網域名稱新增至「`demdex.net`」，如下所示。 如需 `dpm.demdex.net` 呼叫的詳細資訊，請參閱[了解向 Demdex 網域進行的叫呼](https://experienceleague.adobe.com/docs/audience-manager/user-guide/reference/demdex-calls.html?lang=zh-Hant)。

**需求**

若要進行這些設定，您必須使用：

* 貴公司記錄的Audience Manager子網域名稱。 向您的顧問確認或取得此名稱。
* 與您的IMS組織ID相關聯的子網域名稱。
* 具有相同子網域名稱的&#x200B;*兩個*&#x200B;設定參數。

**程式碼範例**

在此範例中，假設有一家媒體娛樂公司對於向 `dpm.demdex.net` 進行的呼叫表達法律上疑慮。 在Audience Manager中，該公司記錄的子網域名稱為Music1。 下列程式碼範例示範如何針對此客戶專屬的子網域名稱來包裝「訪客ID服務」資料呼叫。

```
//Instantiate Visitor 
var visitor = Visitor.getInstance("INSERT-IMS-ORG-ID-HERE",{ 
     ... 
     //Configure Visitor ID Service call 
     audienceManagerServer: "Music1.demdex.net", 
     audienceManagerServerSecure: "Music1.demdex.net" 
     } 
);
```

