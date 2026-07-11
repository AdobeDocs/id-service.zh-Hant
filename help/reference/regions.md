---
description: AMCV Cookie包含網站訪客的ECID和地區ID。 這些 ID 會儲存為機碼值組。 mid user ID保有訪客的ECID。 aamlh region ID 保有網站訪客的地區 ID。 您可透過剖析 AMCV Cookie 來復原此項資訊。
keywords: 訪客 ID 服務
title: 從AMCV Cookie或訪客ID服務取得地區和使用者ID
exl-id: 986e761e-4bc7-4511-86b7-7d13a7761a2b
TQID: https://experienceleague.adobe.com/OBzPrrLffDFgRisA27XIIl33x-4aWmj0krXF3prLPUk
product_v2: id: e1971122-7081-4556-9222-8a31bd71800c
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554id: c66ffd68-0f65-42bb-aa23-b4020f12e0bdid: f8a45b24-4be7-4f1b-909b-60d06b483a20id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2: id: d3cdead0-685a-4489-9250-4bb709942f66
source-git-commit: 09ee359440c122702a6ce83708c98af3862c9cc9
workflow-type: tm+mt
source-wordcount: 235
ht-degree: 42%

---

# 從AMCV Cookie或訪客ID服務取得地區和使用者ID {#get-region-and-user-ids-from-the-amcv-cookie-or-the-id-service}

AMCV Cookie包含網站訪客的ECID和地區ID。 這些 ID 會儲存為機碼值組。 mid:user ID保有訪客的ECID。 aamlh:region ID保有網站訪客的地區ID。 您可透過剖析 AMCV Cookie 來復原此項資訊。

如需詳細資訊，請參閱[透過訪客ID服務取得使用者ID與地區](https://experienceleague.adobe.com/docs/audience-manager/user-guide/api-and-sdk-code/dcs/dcs-apis/dcs-mcid-ids.html?lang=zh-Hant)。

如果您是Audience Manager客戶，您可從資料收集伺服器(DCS)傳送的回應中取得地區ID。 請參閱[從 DCS 回應取得用戶 ID 與地區](https://experienceleague.adobe.com/docs/audience-manager/user-guide/api-and-sdk-code/dcs/dcs-apis/dcs-aam-ids.html?lang=zh-Hant)。

您也可以使用訪客ID服務提供的`GET`方法取得地區ID。 請參閱[取得地區 ID (位置提示)](../library/get-set/getlocationhint.md#reference-a761030ff06c4439946bb56febf42d4c)。

