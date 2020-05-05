---
description: ID要求與回應程式的概述。 這些範例涵蓋在個別網站、跨不同網站，以及針對由不同 Experience Cloud 客戶 (具有自己的組織 ID) 管理的網站，進行 ID 指派。
keywords: ID Service
seo-description: ID要求與回應程式的概述。 這些範例涵蓋在個別網站、跨不同網站，以及針對由不同 Experience Cloud 客戶 (具有自己的組織 ID) 管理的網站，進行 ID 指派。
seo-title: Experience Cloud Identity 服務如何要求與設定 ID
title: Experience Cloud Identity 服務如何要求與設定 ID
uuid: ff7f5b7e-e959-4391-b75c-b7a36286e0ea
translation-type: tm+mt
source-git-commit: d2bc0e7fedc4e48d51f5dad158f9f8bfcb0cb4f3

---


# Experience Cloud Identity 服務如何要求與設定 ID{#how-the-experience-cloud-id-service-requests-and-sets-ids}

ID要求與回應程式的概述。 這些範例涵蓋在個別網站、跨不同網站，以及針對由不同 Experience Cloud 客戶 (具有自己的組織 ID) 管理的網站，進行 ID 指派。

>[!NOTE]
>
>如果您不熟悉 Experience Cloud Identity 服務建立訪客 ID 的方式，請先花點時間檢閱 [Experience Cloud](../introduction/cookies.md)。

**提示：** 另請參閱我們 [的跨網域追蹤ID服務影片](https://helpx.adobe.com/marketing-cloud-core/kb/MCID/CrossDomain.html)。

## 請求 Experience Cloud ID {#section-0b5e261fbd0547d9b9a1680e5ce536cc}

下列範例示範 ID 服務請求和接收 Experience Cloud 訪客 ID 的方式。這些範例使用食品公司和運動公司這兩家虛構公司來示範 ID 要求和回應的資料流程。每間公司都有獨特的 Experience Cloud 組織 ID，並且已經在所有公司網站上實作 ID 服務程式碼。這些使用案例會呈現在未使用 Analytics、舊有 ID 或封鎖第三方 Cookie 的瀏覽器的情況下，一般 ID 服務實作的資料流程。

![](assets/sample_sites.png)

**第一個要求**

在此範例中，新訪客來到食品公司管理的披薩網站。 食品公司在披薩網站上有ID服務程式碼。 當披薩網站載入時，ID服務程式碼會檢查披薩網域中的AMCV Cookie。

* 如果已設定AMCV Cookie，則網站訪客會擁有Experience Cloud ID。 在此情況下，Cookie 會追蹤訪客並與其他 Experience Cloud 解決方案共用資料。
* If the AMCV cookie is not set, the ID service code calls a regional [data collection server](https://docs.adobe.com/content/help/en/analytics/technotes/rdc/regional-data-collection.html) (DCS) at `dpm.demdex.net/id` (see also, [Understanding Calls to the Demdex Domain](https://docs.adobe.com/content/help/zh-Hant/audience-manager/user-guide/reference/demdex-calls.html)). 此呼叫包括食品公司的組織 ID。組織 ID 是在 ID 服務程式碼的 `Visitor.getInstance` 函數中設定。

![](assets/request1.png)

**第一個回應**

回應時，DCS 傳回 [!DNL Experience Cloud] ID (MID) 和 Demdex Cookie。ID服務程式碼會將MID值寫入AMCV Cookie。 例如，假設DCS傳回MID值1234。 AMCV Cookie 將會儲存為 `mid|1234`，並在第一方披薩網域中設定。Demdex Cookie也包含唯一ID（我們稱之為5678）。 此Cookie設定在第三方demdex.net網域中，與披薩網域分開。

![](assets/response1.png)

如您在下個範例中所見，當訪客移至食品公司的其他網站時，Demdex ID和組織ID可讓ID服務建立並傳回正確的MID。

## 跨網站要求和回應 {#section-15ea880453af467abd2874b8b4ed6ee9}

在此範例中，我們的食品公司訪客從披薩網站導覽至墨西哥卷餅網站。 食品公司在墨西哥卷餅網站上有ID服務代碼。 該訪客從未造訪過墨西哥卷餅網站。

基於這些條件，墨西哥卷餅網站上沒有AMCV Cookie。 此外，ID服務無法使用披薩網站上設定的AMCV Cookie，因為它是披薩網域的專屬。 因此，ID服務必須呼叫DCS以檢查並請求訪客ID。 在此例中，DCS呼叫會包含食品公司的組織ID *和* demdex ID。 請記住，Demdex ID是從披薩網站擷取，並儲存為demdex.net網域下的第三方Cookie。

![](assets/request2.png)

在DCS收到組織ID和Demdex ID後，會為我們的網站訪客建立並傳回正確的MID。 由於 是以數學方式從組織 ID 和 Demdex ID 計算得來，因此 AMCV Cookie 包含 MID 值 `mid = 1234`mid = 。

![](assets/response2.png)

## 來自其他網站的 ID 要求 {#section-ba9a929e50d64b0aba080630fd83b6f1}

在此範例中，我們的訪客離開食品公司網站並導覽至體育公司擁有的足球網站。 當訪客造訪足球網站時，ID檢查和要求程式的運作方式與先前範例中所述相同。 不過，由於Sports Company有其專屬的組織ID，因此ID服務會傳回不同的MID。 新的 MID 專屬於運動公司控管的網域，可讓企業在 [!DNL Experience Cloud] 的各解決方案中追蹤和共用訪客資料。該名訪客的 Demdex ID 仍維持不變，因為 Demdex ID 包含在第三方 Cookie 中，且會在不同網域中持續存在。

![](assets/req_resp.png)

