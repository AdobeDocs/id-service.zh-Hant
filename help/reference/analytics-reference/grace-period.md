---
description: 如果您有多個 JavaScript 檔案會傳送資料至相同的報表套裝，或是您要在網站上使用其他技術 (例如 Flash 視訊測量)，建議您設定寬限期。
keywords: ID Service
seo-description: 如果您有多個 JavaScript 檔案會傳送資料至相同的報表套裝，或是您要在網站上使用其他技術 (例如 Flash 視訊測量)，建議您設定寬限期。
seo-title: ID 服務寬限期
title: ID 服務寬限期
uuid: 10a7db7d-de32-4379-914f-edaf929efa32
translation-type: tm+mt
source-git-commit: bc5c81455023e22e64877bb861dfe141e158599c
workflow-type: tm+mt
source-wordcount: '456'
ht-degree: 68%

---


# ID 服務寬限期 {#the-id-service-grace-period}

如果您有多個 JavaScript 檔案會傳送資料至相同的報表套裝，或是您要在網站上使用其他技術 (例如 Flash 視訊測量)，建議您設定寬限期。

在您部署 [!DNL Experience Cloud] ID 服務後，新的訪客將不會再從您的資料收集伺服器接收 Analytics 訪客 ID。如果您的網站有某些區段尚未實作 [!DNL Experience Cloud] ID 服務，當訪客瀏覽到這些區段時，將無法辨識 Experience Cloud ID，並且系統會為訪客指派舊有的 Analytics 訪客 ID。這可能會建立重複的瀏覽計數和不正確的歸因。

例如，若您網站的支援區段是在獨立的 CMS 中進行管理，則此區段的 Analytics JavaScript 檔案可能會不同。如果您在將訪客ID服務部署至支援網站之前，先將訪客ID部署在主網站上，新訪客在造訪支援區段時會收到舊有的Analytics ID，而跨兩個網站區段的造訪將會報告為不同的造訪。

將 [!DNL Experience Cloud] ID 服務部署在使用多個 JavaScript 檔案或其他技術 (例如 Flash) 的網站上，可能會導致協調方面的問題，因為您必須同時在網站的所有區段上啟用 ID 服務。藉由寬限期的設定，新訪客將繼續從 [!DNL Experience Cloud] ID 服務接收 Analytics 訪客 ID，因而可在您未升級為使用 ID 服務的網站區段上持續識別訪客。

>[!NOTE]
>
>必須使用 1.3 版或更新版本的 [!DNL Experience Cloud] ID 服務，才支援寬限期。

## 我是否需要寬限期? {#section-fd34c7ff697348a39f49258b7d39eb42}

如果您有單一Analytics JavaScript檔案，且未使用任何其他AppMeasurement程式庫，則不需要寬限期。 您可以在單一JavaScript檔案中進行更新，而且新訪客在瀏覽期間會使用Marketing Cloud ID一致地加以識別。

If you have multiple JavaScript files that are sending data to the *same report suite*, or if you are using other technologies on your site such as Flash video measurement, we recommend configuring a grace period.

## 如何啟用寬限期?   {#section-512d5cd8570e483cbdd8b04457a16ced}

Contact [Customer Care](https://helpx.adobe.com/tw/marketing-cloud/contact-support.html).
