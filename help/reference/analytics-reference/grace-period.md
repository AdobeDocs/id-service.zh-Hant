---
description: 如果您有多個 JavaScript 檔案會傳送資料至相同報表套裝，或是您在網站上使用其他技術 (例如 Flash 影片測量)，我們建議您設定寬限期。
keywords: ID 服務
title: ID 服務寬限期
exl-id: 83b4898c-8358-458b-a798-1e3c9633afe9
source-git-commit: 06e935a4ba4776baa900d3dc91e294c92b873c0f
workflow-type: tm+mt
source-wordcount: '417'
ht-degree: 100%

---

# ID 服務寬限期 {#the-id-service-grace-period}

如果您有多個 JavaScript 檔案會傳送資料至相同報表套裝，或是您在網站上使用其他技術 (例如 Flash 影片測量)，我們建議您設定寬限期。

在您部署 [!DNL Experience Cloud] ID 服務後，新的訪客將不會再從您的資料收集伺服器接收 Analytics 訪客 ID。如果您的網站有某些區段尚未實作 [!DNL Experience Cloud] ID 服務，當訪客瀏覽到這些區段時，將無法辨識 Experience Cloud ID，並且系統會為訪客指派舊有的 Analytics 訪客 ID。這可能會產生重複造訪計數及不正確的歸因。

舉例來說，若您網站的支援區段是在個別 CMS 中進行管理，則此區段的 Analytics JavaScript 檔案可能會不同。如果您在將訪客 ID 服務部署至支援網站之前，先在主網站上部署了訪客 ID，則新訪客在造訪支援區段時會收到舊有的 Analytics ID，而跨兩個網站區段的造訪則會報告為不同的造訪。

將 [!DNL Experience Cloud] ID 服務部署在使用多個 JavaScript 檔案或其他技術 (例如 Flash) 的網站上，可能會導致協調方面的問題，因為您必須同時在網站的所有區段上啟用 ID 服務。藉由寬限期的設定，新訪客將繼續從 [!DNL Experience Cloud] ID 服務接收 Analytics 訪客 ID，因而可在您未升級為使用 ID 服務的網站區段上持續識別訪客。

>[!NOTE]
>
>必須使用 1.3 版或更新版本的 [!DNL Experience Cloud] ID 服務，才支援寬限期。

## 我是否需要寬限期? {#section-fd34c7ff697348a39f49258b7d39eb42}

如果您有單一 Analytics JavaScript 檔案，而且並未使用其他任何 AppMeasurement 程式庫，您就不需要寬限期。您可以在單一 JavaScript 檔案中進行更新，系統將會在新訪客造訪期間使用 Marketing Cloud ID 一致地識別他們。

如果您有多個 JavaScript 檔案會傳送資料至&#x200B;*相同報表套裝*，或是您在網站上使用其他技術 (例如 Flash 影片測量)，我們建議您設定寬限期。

## 如何啟用寬限期?   {#section-512d5cd8570e483cbdd8b04457a16ced}

請聯絡[客戶服務](https://helpx.adobe.com/tw/marketing-cloud/contact-support.html)。
