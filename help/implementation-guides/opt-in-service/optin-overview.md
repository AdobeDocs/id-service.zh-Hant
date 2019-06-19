---
description: 選擇加入服務可讓您設定訪客的通訊協定，以判斷您在瀏覽您的網站時是否可以在使用者裝置或瀏覽器上設定Cookie。
seo-description: 選擇加入服務可讓您設定訪客的通訊協定，以判斷您在瀏覽您的網站時是否可以在使用者裝置或瀏覽器上設定Cookie。
seo-title: 選擇加入服務
title: 選擇加入服務
uuid: aubd72ad-4118-471b-9755-d08 a72 a72 ca0 d
translation-type: tm+mt
source-git-commit: bc5c81455023e22e64877bb861dfe141e158599c

---


# 選擇加入服務{#opt-in-service}

選擇加入服務可讓您設定訪客的通訊協定，以判斷您在瀏覽您的網站時是否可以在使用者裝置或瀏覽器上設定Cookie。

選擇加入服務是 [Experience Cloud ID(ECID)](https://marketing.adobe.com/resources/help/en_US/mcvid/) 服務的擴充功能，其設計可讓您控制在使用者同意之前，是否能針對訪客在網頁上建立Cookie。選擇加入服務也可讓您設定通訊協定，以便與您的同意管理平台(CMP)和現有系統整合，做為大型設計的一部分。

使用選擇加入服務，您可以指定訪客可以一次選擇加入Adobe解決方案，或依順序顯示解決方案。客戶完成並記錄核准程序後，您便可以從所有的 Adobe 解決方案擷取 CMP 訪客核准。

使用Adobe [Launch](https://docs.adobelaunch.com/) 搭配 [選擇加入擴充功能](../../implementation-guides/opt-in-service/launch.md)，即可輕鬆實作和設定加入服務。它也可以使用 [DTM實施和設定](../../implementation-guides/opt-in-service/optin-dtm.md)。

請參閱 [設定加入服務](../../implementation-guides/opt-in-service/getting-started.md) 以開始使用。

>[!NOTE]
>
>選擇加入服務可讓您設定系統以批准或拒絕下載Adobe Cookie。不提供收集使用者同意偏好設定的支援，也並非偏好設定的存放庫。

>[!IMPORTANT]
>
>本文內容不是法律建議，也不是用來取代法律建議。設定選擇加入實作時，請向貴公司的法務部門諮詢同意與實務的相關建議。

## 所有 Experience Cloud 解決方案的選擇加入 {#section-053e6224505542cf961896f0ca869e52}

選擇加入服務是根據您自己的需求建立同意選擇的工具，讓您在徵得用戶或同意控制器同意之前，設計工作流程以回應(引發標籤)。

選擇加入服務可讓您為Adobe解決方案設定許可管理實務：

* 指出在大部分情況下，同意收集要求是否適用於使用者。
* 指定哪個解決方案允許產生 Cookie。
* 為使用者未明確同意或拒絕類別的解決方案，套用預設偏好設定。
* 根據使用者同意設定的變更內容，觸發自訂回應，讓您可以保留或更新使用者設定。

使用選擇加入服務，您可以設定您的網站，讓某些Cookie在使用者選擇之前預先取得同意。您可以為新客戶設定選擇加入服務，以便在使用者同意後或在提供選擇後載入Cookie。您也可以從現有的同意管理平台儲存或擷取選擇加入同意，或僅將選擇加入權限儲存在 Cookie。

![](assets/Opt-in-approval.png)

Adobe 解決方案接著便可檢查標籤是否通過核准，然後訂閱變更內容，最後擷取所有的選擇加入客戶。選擇加入服務可讓您透過解決方案JavaScript程式庫或透過ECID直接取得權限。
