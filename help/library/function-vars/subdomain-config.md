---
description: 使用這些設定，可將呼叫 Experience Cloud 身分識別服務使用的預設網域名稱變更為您擁有的子網域名稱。
keywords: ID 服務
title: audienceManagerServer 及 audienceManagerServerSecure
exl-id: b740eb5c-ac4e-46f4-ba7c-1080d8d9292d
TQID: https://experienceleague.adobe.com/a5KVErDX4putY8d9vGf-uAwswNzE0Maf-JEyfmQxhbg
product_v2: id: e1971122-7081-4556-9222-8a31bd71800c
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554id: c66ffd68-0f65-42bb-aa23-b4020f12e0bdid: f8a45b24-4be7-4f1b-909b-60d06b483a20id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
source-git-commit: 5c41e39a833b527a329f62e5f0929445f47139de
workflow-type: tm+mt
source-wordcount: 222
ht-degree: 100%

---

# audienceManagerServer 及 audienceManagerServerSecure{#audiencemanagerserver-and-audiencemanagerserversecure}

使用這些設定，可將呼叫 Experience Cloud 身分識別服務使用的預設網域名稱變更為您擁有的子網域名稱。

**語法:**

* `audienceManagerServer: " *`您的子網域名稱`*.demdex.net"`
* `audienceManagerServerSecure: " *`您的子網域名稱`*.demdex.net"`

**用途**

[!DNL Experience Cloud] ID 服務通常會在 [!DNL Adobe] 呼叫 `dpm.demdex.net`。 有時候，您會覺得此目的地看起來太普遍或太像「第三方」而不想進行呼叫。 要讓 ID 服務呼叫看起來更像第一方呼叫，您可以使用這些設定將您的 [!DNL Audience Manager] 子網域名稱新增到 `demdex.net`，如下所示。 如需 `dpm.demdex.net` 呼叫的詳細資訊，請參閱[了解向 Demdex 網域進行的叫呼](https://experienceleague.adobe.com/docs/audience-manager/user-guide/reference/demdex-calls.html?lang=zh-Hant)。

**需求**

若要進行這些設定，您必須使用：

* 貴公司記錄的 [!DNL Audience Manager] 子網域名稱。 向您的顧問確認或取得此名稱。
* 與您的[!UICONTROL Organization ID] 相關聯的子網域名稱。
* 具有相同子網域名稱的&#x200B;*兩個*&#x200B;設定參數。

**程式碼範例**

在此範例中，假設有一家媒體娛樂公司對於向 `dpm.demdex.net` 進行的呼叫表達法律上疑慮。 在 [!DNL Audience Manager] 中，該公司記錄的子網域名稱為「Music1」。 下列程式碼範例示範如何針對此客戶專屬的子網域名稱來包裝 ID 服務資料呼叫。

```
//Instantiate Visitor 
var visitor = Visitor.getInstance("Insert Experience Cloud Organization ID here",{ 
     ... 
     //Configure ID service call 
     audienceManagerServer: "Music1.demdex.net", 
     audienceManagerServerSecure: "Music1.demdex.net" 
     } 
);
```

