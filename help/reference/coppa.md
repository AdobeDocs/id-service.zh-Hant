---
description: 兒童網路隱私保護法 (COPPA) 禁止在未經父母明確同意下，透過網路收集 13 歲以下兒童的個人資訊。客戶擔憂 COPPA 會在 Experience Cloud Identity 服務程式碼中新增選用變數，使該程式碼無法在第三方瀏覽器網域中設定 Cookie。
keywords: ID 服務
seo-description: 兒童網路隱私保護法 (COPPA) 禁止在未經父母明確同意下，透過網路收集 13 歲以下兒童的個人資訊。客戶擔憂 COPPA 會在 Experience Cloud Identity 服務程式碼中新增選用變數，使該程式碼無法在第三方瀏覽器網域中設定 Cookie。
seo-title: Experience Cloud Identity 服務的 COPPA 支援
title: Experience Cloud Identity 服務的 COPPA 支援
uuid: 621b5ebd-92e7-4635-be85-8d7e36589fcb
translation-type: tm+mt
source-git-commit: c4c0b791230422f17292b72fd45ba5689a60adae

---


# Experience Cloud Identity 服務的 COPPA 支援 {#coppa-support-in-the-experience-cloud-id-service}

兒童網路隱私保護法 (COPPA) 禁止在未經父母明確同意下，透過網路收集 13 歲以下兒童的個人資訊。客戶擔憂 COPPA 會在 Experience Cloud Identity 服務程式碼中新增選用變數，使該程式碼無法在第三方瀏覽器網域中設定 Cookie。

>[!NOTE]
>
>適用於 3.0.0 版或更高版本。

**Cookie 與追蹤**

當網頁載入時，[!DNL Experience Cloud] ID 服務會呼叫 [!DNL Adobe] 資料收集伺服器 (DCS)。DCS 回應包括 Experience Cloud Cookie 與 demdex.net Cookie。

* 已在第一方網域設定 Experience Cloud Cookie。其無法用於追蹤不同網域的訪客，除非這些網域共同允許存取。
* 已在第三方網域設定 demdex.net Cookie。它包含了可用於追蹤不同網域訪客的獨特識別碼。

**Cookie 與 COPPA 法規**

若在以兒童為導向或主要針對兒童的網站上，發現追蹤不同網域訪客的第三方 Cookie，會觸發 COPPA 父母同意需求。為了更輕鬆遵守 COPPA 以供內部網站分析使用，請將變數 `disableThirdPartyCookies:true` 新增至 `Visitor.getInstance` 函數，如下所示。

```js
//Call the ID service 
var visitor = Visitor.getInstance("insert marketing cloud ID here", { 
 
    //Set disableThirdPartyCookies configuration param 
    disableThirdPartyCookies: true 
 
    ... 
});
```

設為 `true` 時，`disableThirdPartyCookies` 物件會阻止 DCS 傳回第三方的 demdex.net Cookie。如果網站訪客在瀏覽器中已擁有此 Cookie，ID 服務不會使用該 Cookie 來建立新的 [!DNL Experience Cloud] ID 或傳回現有 ID。相反地，[!DNL Experience Cloud] ID 服務會在第一方 Cookie 中建立新的隨機 ID。啟用後，您可以利用 ID 服務收集資料，並在不同的 [!DNL Experience Cloud] 解決方案之間共用資料，包括 COPPA 允許的其他內部作業。

>[!MORELIKETHIS]
>
>* [Adobe 隱私中心](http://www.adobe.com/privacy.html)
>* [什麼是 COPPA? ](http://www.consumer.ftc.gov/articles/0031-protecting-your-childs-privacy-online#whatis)

