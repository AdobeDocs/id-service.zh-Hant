---
description: 兒童網路隱私保護法(COPPA)禁止在未經父母明確同意下，透過網路收集13歲以下兒童的個人資訊。 客戶擔憂COPPA會在「訪客ID服務」程式碼中新增選用變數，使該程式碼無法在第三方瀏覽器網域中設定Cookie。
keywords: 訪客 ID 服務
title: Adobe訪客ID服務的COPPA支援
exl-id: c7579f90-3011-4e26-b908-08907bf12ba2
TQID: https://experienceleague.adobe.com/szz7syrA2KSDasXTox02PTbxBy60tfFc80hHmsjXwc0
product_v2: id: e1971122-7081-4556-9222-8a31bd71800c
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554id: c66ffd68-0f65-42bb-aa23-b4020f12e0bdid: f8a45b24-4be7-4f1b-909b-60d06b483a20id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2: id: d095671a-1355-40aa-8b5f-06c33c68080bid: d3cdead0-685a-4489-9250-4bb709942f66id: f4e6943a-c91a-4134-a2c7-f4f20cfff2f0
source-git-commit: 09ee359440c122702a6ce83708c98af3862c9cc9
workflow-type: tm+mt
source-wordcount: 363
ht-degree: 36%

---

# Adobe訪客ID服務的COPPA支援 {#coppa-support-in-the-experience-cloud-id-service}

兒童網路隱私保護法(COPPA)禁止在未經父母明確同意下，透過網路收集13歲以下兒童的個人資訊。 客戶擔憂COPPA會在「訪客ID服務」程式碼中新增選用變數，使該程式碼無法在第三方瀏覽器網域中設定Cookie。

>[!NOTE]
>
>適用於 3.0.0 版或更高版本。

**Cookie 與追蹤**

當網頁載入時，訪客ID服務會呼叫Adobe資料收集伺服器(DCS)。 DCS回應包含CX Enterprise Cookie和demdex.net Cookie。

* CX Enterprise Cookie設定在第一方網域中。 它無法用於追蹤不同網域的訪客，除非這些網域一起合作來允許存取。
* demdex.net Cookie 是在第三方網域中所設定。 它包含可用於追蹤不同網域的訪客的唯一識別碼。

**Cookie 與 COPPA 合規性**

在導向 (或主要適用於) 兒童的網站上的不同網域中追蹤訪客的第三方 Cookie 會觸發 COPPA 家長同意的要求。 為了更輕鬆遵守 COPPA 以供內部網站分析使用，請將變數 `disableThirdPartyCookies:true` 新增至 `Visitor.getInstance` 函數，如下所示。

```js
//Call the Visitor ID Service 
var visitor = Visitor.getInstance("insert marketing cloud ID here", { 
 
    //Set disableThirdPartyCookies configuration param 
    disableThirdPartyCookies: true 
 
    ... 
});
```

設為 `true` 時，`disableThirdPartyCookies` 物件會阻止 DCS 傳回第三方的 demdex.net Cookie。 如果網站訪客的瀏覽器中已有此Cookie，「訪客ID服務」就不會使用它來建立新的ECID或傳回現有的ID。 訪客ID服務而是會在第一方Cookie中建立新的隨機ID。 啟用後，您可以使用訪客ID服務收集資料，並在不同的CX Enterprise解決方案之間共用資料，包括COPPA允許的其他內部作業。

>[!MORELIKETHIS]
>
>* [Adobe 隱私中心](https://www.adobe.com/tw/privacy.html)
>* [什麼是 COPPA? ](http://www.consumer.ftc.gov/articles/0031-protecting-your-childs-privacy-online#whatis)

