---
description: 使用這些設定，可將呼叫 Experience Cloud Identity Service 使用的預設網域名稱變更為您擁有的子網域名稱。
keywords: ID 服務
title: audienceManagerServer 及 audienceManagerServerSecure
exl-id: b740eb5c-ac4e-46f4-ba7c-1080d8d9292d
source-git-commit: cb89ac70e37f35d5e4e2b971f2df9645304522f8
workflow-type: tm+mt
source-wordcount: '212'
ht-degree: 100%

---

# audienceManagerServer 及 audienceManagerServerSecure{#audiencemanagerserver-and-audiencemanagerserversecure}

使用這些設定，可將呼叫 Experience Cloud Identity Service 使用的預設網域名稱變更為您擁有的子網域名稱。

**語法:**

* ` audienceManagerServer: " *`您的子網域名稱`*.demdex.net"`
* ` audienceManagerServerSecure: " *`您的子網域名稱`*.demdex.net"`

**用途**

[!DNL Experience Cloud] ID 服務通常會在 [!DNL Adobe] 呼叫 `dpm.demdex.net`。有時候，您會覺得此目的地看起來太普遍或太像「第三方」而不想進行呼叫。要讓 ID 服務呼叫看起來更像第一方呼叫，您可以使用這些設定將您的 [!DNL Audience Manager] 子網域名稱新增到 `demdex.net`，如下所示。如需 `dpm.demdex.net` 呼叫的詳細資訊，請參閱[了解向 Demdex 網域進行的叫呼](https://experienceleague.adobe.com/docs/audience-manager/user-guide/reference/demdex-calls.html?lang=zh-Hant)。

**需求**

若要進行這些設定，您必須使用：

* 貴公司記錄的 [!DNL Audience Manager] 子網域名稱。向您的顧問確認或取得此名稱。
* 與您的[!UICONTROL 組織 ID] 相關聯的子網域名稱。
* 具有相同子網域名稱的&#x200B;*兩個*&#x200B;設定參數。

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
