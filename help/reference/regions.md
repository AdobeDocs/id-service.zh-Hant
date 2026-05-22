---
description: AMCV Cookie 包含網站訪客的 Experience Cloud ID (MID) 和地區 ID。 這些 ID 會儲存為機碼值組。 mid user ID 保有訪客的 Experience Cloud ID。 aamlh region ID 保有網站訪客的地區 ID。 您可透過剖析 AMCV Cookie 來復原此項資訊。
keywords: ID 服務
title: 從 AMCV Cookie 或 ID 服務取得地區和用戶 ID
exl-id: 986e761e-4bc7-4511-86b7-7d13a7761a2b
TQID: https://experienceleague.adobe.com/OBzPrrLffDFgRisA27XIIl33x-4aWmj0krXF3prLPUk
product_v2:
  - id: e1971122-7081-4556-9222-8a31bd71800c
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: f8a45b24-4be7-4f1b-909b-60d06b483a20
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2:
  - id: d3cdead0-685a-4489-9250-4bb709942f66
source-git-commit: 5c41e39a833b527a329f62e5f0929445f47139de
workflow-type: tm+mt
source-wordcount: 240
ht-degree: 91%

---

# 從 AMCV Cookie 或 ID 服務取得地區和用戶 ID {#get-region-and-user-ids-from-the-amcv-cookie-or-the-id-service}

AMCV Cookie 包含網站訪客的 Experience Cloud ID (MID) 和地區 ID。 這些 ID 會儲存為機碼值組。 mid:user ID保有訪客的Experience Cloud ID。 aamlh:region ID保有網站訪客的地區ID。 您可透過剖析 AMCV Cookie 來復原此項資訊。

如需詳細資訊，請參閱[透過 Experience Cloud 身分識別服務取得使用者 ID 與地區](https://experienceleague.adobe.com/docs/audience-manager/user-guide/api-and-sdk-code/dcs/dcs-apis/dcs-mcid-ids.html?lang=zh-Hant)。

如果您是 [!DNL Audience Manager] 客戶，您可從資料收集伺服器 (DCS) 傳送的回應中取得地區 ID。 請參閱[從 DCS 回應取得用戶 ID 與地區](https://experienceleague.adobe.com/docs/audience-manager/user-guide/api-and-sdk-code/dcs/dcs-apis/dcs-aam-ids.html?lang=zh-Hant)。

您也可以利用 ID 服務提供的 `GET` 方法取得地區 ID。 請參閱[取得地區 ID (位置提示)](../library/get-set/getlocationhint.md#reference-a761030ff06c4439946bb56febf42d4c)。

