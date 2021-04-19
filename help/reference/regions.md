---
description: AMCV Cookie 包含網站訪客的 Experience Cloud ID (MID) 和地區 ID。這些 ID 會儲存為機碼值組。mid user ID 保有訪客的 Experience Cloud ID。aamlh region ID 保有網站訪客的地區 ID。您可透過剖析 AMCV Cookie 來復原此項資訊。
keywords: ID 服務
seo-description: AMCV Cookie 包含網站訪客的 Experience Cloud ID (MID) 和地區 ID。這些 ID 會儲存為機碼值組。mid user ID 保有訪客的 Experience Cloud ID。aamlh region ID 保有網站訪客的地區 ID。您可透過剖析 AMCV Cookie 來復原此項資訊。
seo-title: 從 AMCV Cookie 或 ID 服務取得地區和用戶 ID
title: 從 AMCV Cookie 或 ID 服務取得地區和用戶 ID
uuid: bdd9d001-f29f-4ff0-800b-8182243da218
exl-id: 986e761e-4bc7-4511-86b7-7d13a7761a2b
translation-type: ht
source-git-commit: 4453ebf701ea2dc06e6093dd77be6eb0f3b2936e
workflow-type: ht
source-wordcount: '297'
ht-degree: 100%

---

# 從 AMCV Cookie 或 ID 服務取得地區和用戶 ID {#get-region-and-user-ids-from-the-amcv-cookie-or-the-id-service}

AMCV Cookie 包含網站訪客的 Experience Cloud ID (MID) 和地區 ID。這些 ID 會儲存為機碼值組。mid:user ID 保有訪客的 Experience Cloud ID。aamlh:region ID 保有網站訪客的地區 ID。您可透過剖析 AMCV Cookie 來復原此項資訊。

如需詳細資訊，請參閱[透過 Experience Cloud Identity Service 取得用戶 ID 與地區](https://docs.adobe.com/content/help/zh-Hant/audience-manager/user-guide/api-and-sdk-code/dcs/dcs-apis/dcs-mcid-ids.html)。

如果您是 [!DNL Audience Manager] 客戶，您可從資料收集伺服器 (DCS) 傳送的回應中取得地區 ID。請參閱[從 DCS 回應取得用戶 ID 與地區](https://docs.adobe.com/content/help/zh-Hant/audience-manager/user-guide/api-and-sdk-code/dcs/dcs-apis/dcs-aam-ids.html)。

您也可以利用 ID 服務提供的 `GET` 方法取得地區 ID。請參閱[取得地區 ID (位置提示)](../library/get-set/getlocationhint.md#reference-a761030ff06c4439946bb56febf42d4c)。
