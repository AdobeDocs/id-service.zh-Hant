---
description: AMCV Cookie包含網站訪客的Experience Cloud ID(MID)和地區ID。 這些ID會儲存為索引鍵值配對。 mid user ID 保有訪客的 Experience Cloud ID。aamlh region ID 保有網站訪客的地區 ID。您可透過剖析 AMCV Cookie 來復原此項資訊。
keywords: ID Service
seo-description: AMCV Cookie包含網站訪客的Experience Cloud ID(MID)和地區ID。 這些ID會儲存為索引鍵值配對。 mid user ID 保有訪客的 Experience Cloud ID。aamlh region ID 保有網站訪客的地區 ID。您可透過剖析 AMCV Cookie 來復原此項資訊。
seo-title: 從 AMCV Cookie 或 ID 服務取得地區和使用者 ID
title: 從 AMCV Cookie 或 ID 服務取得地區和使用者 ID
uuid: bdd9d001-f29f-4ff0-800b-8182243da218
translation-type: tm+mt
source-git-commit: d2bc0e7fedc4e48d51f5dad158f9f8bfcb0cb4f3

---


# 從 AMCV Cookie 或 ID 服務取得地區和使用者 ID {#get-region-and-user-ids-from-the-amcv-cookie-or-the-id-service}

AMCV Cookie包含網站訪客的Experience Cloud ID(MID)和地區ID。 這些ID會儲存為索引鍵值配對。 mid:user ID會保留訪客的Experience Cloud ID。 aamlh:region ID會保留您網站訪客的地區ID。 您可透過剖析 AMCV Cookie 來復原此項資訊。

For more information, see [Get User IDs and Regions Through the Experience Cloud Identity Service](https://docs.adobe.com/content/help/en/audience-manager/user-guide/api-and-sdk-code/dcs/dcs-apis/dcs-mcid-ids.html).

如果您是 [!DNL Audience Manager] 客戶，您可從資料收集伺服器 (DCS) 傳送的回應中取得地區 ID。See [Get User IDs and Regions from a DCS Response](https://docs.adobe.com/content/help/en/audience-manager/user-guide/api-and-sdk-code/dcs/dcs-apis/dcs-aam-ids.html).

您也可以利用 ID 服務提供的 `GET` 方法取得地區 ID。請參閱[取得地區 ID (位置提示)](../library/get-set/getlocationhint.md#reference-a761030ff06c4439946bb56febf42d4c)。
