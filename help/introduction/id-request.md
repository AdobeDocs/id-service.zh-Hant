---
description: 概述 ID 請求與回應程序。這些範例涵蓋在個別網站、跨不同網站，以及針對由不同 Experience Cloud 客戶 (具有自己的組織 ID) 管理的網站，進行 ID 指派。
keywords: ID 服務
seo-description: 概述 ID 請求與回應程序。這些範例涵蓋在個別網站、跨不同網站，以及針對由不同 Experience Cloud 客戶 (具有自己的組織 ID) 管理的網站，進行 ID 指派。
seo-title: Experience Cloud Identity Service要求和設定ID的方式
title: Experience Cloud Identity Service要求和設定ID的方式
uuid: ff7f5b7e-e959-4391-b75c-b7a36286e0ea
translation-type: tm+mt
source-git-commit: e6d65f1bfed187d7440512e8f3c2de0550506c95

---


# How the Experience Cloud Identity Service requests and sets IDs{#how-the-experience-cloud-id-service-requests-and-sets-ids}

概述 ID 請求與回應程序。這些範例涵蓋在個別網站、跨不同網站，以及針對由不同 Experience Cloud 客戶 (具有自己的組織 ID) 管理的網站，進行 ID 指派。

>[!NOTE]
>
>If you're not familiar with how the Experience Cloud Identity Service creates the visitor ID, take a moment to review [Experience Cloud](../introduction/cookies.md).

**提示:** 請參閱[跨網域追蹤的 ID 服務影片](https://helpx.adobe.com/marketing-cloud-core/kb/MCID/CrossDomain.html)。

## 請求 Experience Cloud ID {#section-0b5e261fbd0547d9b9a1680e5ce536cc}

下列範例示範 ID 服務請求和接收 Experience Cloud 訪客 ID 的方式。這些範例使用食品公司和運動公司這兩家虛構公司來示範 ID 要求和回應的資料流程。每間公司都有獨特的 Experience Cloud 組織 ID，並且已經在所有公司網站上實作 ID 服務程式碼。這些使用案例會呈現在未使用 Analytics、舊有 ID 或封鎖第三方 Cookie 的瀏覽器的情況下，一般 ID 服務實作的資料流程。

![](assets/sample_sites.png)

**第一個要求**

在此範例中，新訪客造訪食品公司管理的披薩網站。食品公司的披薩網站上擁有 ID 服務程式碼。當披薩網站載入時，ID 服務程式碼會檢查披薩網域中的 AMCV Cookie。

* 如果已設定 AMCV Cookie，網站訪客會擁有 Experience Cloud ID。在此情況下，Cookie 會追蹤訪客並與其他 Experience Cloud 解決方案共用資料。
* 如果尚未設置 AMCV Cookie，則 ID 服務程式碼將在 [ 中呼叫區域 ](https://marketing.adobe.com/resources/help/en_US/aam/?f=c_compcollect.html)資料收集服務器`dpm.demdex.net/id` (DCS) (亦請參閱[瞭解向 Demdex 網域進行的呼叫](https://marketing.adobe.com/resources/help/en_US/aam/demdex-calls.html))。此呼叫包括食品公司的組織 ID。組織 ID 是在 ID 服務程式碼的 `Visitor.getInstance` 函數中設定。

![](assets/request1.png)

**第一個回應**

回應時，DCS 傳回 [!DNL Experience Cloud] ID (MID) 和 Demdex Cookie。ID 服務程式碼將 MID 值寫入 AMCV Cookie。例如 DCS 傳回 1234 的 MID 值。AMCV Cookie 將會儲存為 `mid|1234`，並在第一方披薩網域中設定。Demdex Cookie 也包含獨特的 ID (將其稱為 5678)。此 Cookie 會在第三方 demdex.net 網域中設定，與披薩網域加以區別。

![](assets/response1.png)

如同下一個範例所示，當訪客前往食品公司所屬的另一個網站時，Demdex ID 和組織 ID 都可讓 ID 服務建立和傳回正確的 MID。

## 跨網站要求和回應 {#section-15ea880453af467abd2874b8b4ed6ee9}

在此範例中，食品公司訪客從披薩網站導覽至墨西哥捲餅網站。食品公司的墨西哥捲餅網站上擁有 ID 服務程式碼。該名訪客從未造訪過墨西哥捲餅網站。

有鑑於此，墨西哥捲餅網站上沒有 AMCV Cookie。而 ID 服務無法使用披薩網站中設定的 AMCV Cookie，因為該 Cookie 為披薩網域專屬。因此，ID 服務必須呼叫 DCS 檢查並請求訪客 ID。此時 DCS 呼叫包含食品公司的組織 ID *和* Demdex ID。切記，會從披薩網站中挑取 Demdex ID，並且在 demdex.net 網域下儲存為第三方 Cookie。

![](assets/request2.png)

DCS 收到組織 ID 和 demdex ID 後，會針對網站訪客建立並傳回正確的 MID。由於 是以數學方式從組織 ID 和 Demdex ID 計算得來，因此 AMCV Cookie 包含 MID 值 `mid = 1234`mid = 。

![](assets/response2.png)

## 來自其他網站的 ID 要求 {#section-ba9a929e50d64b0aba080630fd83b6f1}

在此範例中，訪客離開食品公司網站，並導覽至運動公司所擁有的足球網站。當訪客造訪足球網站時，ID 檢查和請求程序會依上一個範例所述的相同方式運作。但是由於運動公司擁有自己的組織 ID，因此 ID 服務會傳回不同的 MID。新的 MID 專屬於運動公司控管的網域，可讓企業在 [!DNL Experience Cloud] 的各解決方案中追蹤和共用訪客資料。該名訪客的 Demdex ID 仍維持不變，因為 Demdex ID 包含在第三方 Cookie 中，且會在不同網域中持續存在。

![](assets/req_resp.png)

