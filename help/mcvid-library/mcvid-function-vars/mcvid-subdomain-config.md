---
description: 使用這些設定，將呼叫 Experience Cloud ID 服務使用的預設網域名稱變更為您擁有的子網域名稱。
keywords: ID 服務
seo-description: 使用這些設定，將呼叫 Experience Cloud ID 服務使用的預設網域名稱變更為您擁有的子網域名稱。
seo-title: audienceManagerServer 及 audienceManagerServerSecure
title: audienceManagerServer 及 audienceManagerServerSecure
uuid: e21caccf-5151-4d34-b0 f7-1e90275 f4 c7 c
translation-type: tm+mt
source-git-commit: bb687c1cd14aae7faef2565dcf9d041a1c06e3bd

---


# audienceManagerServer 及 audienceManagerServerSecure{#audiencemanagerserver-and-audiencemanagerserversecure}

使用這些設定，將呼叫 Experience Cloud ID 服務使用的預設網域名稱變更為您擁有的子網域名稱。

**語法:**

* ` audienceManagerServer: " *`您的子網域名稱`*.demdex.net"`
* ` audienceManagerServerSecure: " *`您的子網域名稱`*.demdex.net"`

**用途**

正常情況下 [!DNL Experience Cloud] ，ID服務會 [!DNL Adobe] 進行呼叫 `dpm.demdex.net`。有時候，您會覺得此目的地看起來太普遍或太像「第三方」而不想進行呼叫。要讓 ID 服務呼叫看起來更像第一方呼叫，您可以使用這些設定將您的 [!DNL Audience Manager] 子網域名稱新增到 `demdex.net`，如下所示。如需關於 `dpm.demdex.net` 呼叫的詳細資訊，請參閱[瞭解向 Demdex 網域進行的呼叫](https://marketing.adobe.com/resources/help/en_US/aam/demdex-calls.html)。

**需求**

這些設定要求您使用:

* 您公司的記錄 [!DNL Audience Manager] 子網域名稱。向您的顧問確認或取得此名稱。
* 與您 [!DNL Organization ID]關聯的子網域名稱。
* *兩個*設定參數均具備相同的子網域名稱。

**程式碼範例**

在此範例中，假設有一家媒體娛樂公司對於向 `dpm.demdex.net` 進行的呼叫表達法律上疑慮。在 [!DNL Audience Manager] 中，該公司記錄的子網域名稱為「Music1」。下列程式碼範例示範如何針對此客戶專屬的子網域名稱來包裝 ID 服務資料呼叫。

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

