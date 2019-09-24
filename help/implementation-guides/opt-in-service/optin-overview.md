---
description: 如果您可以在使用者造訪網站時，在他們的裝置或瀏覽器上設定 Cookie，則選擇加入服務可讓您設定訪客的通訊協定。
seo-description: 如果您可以在使用者造訪網站時，在他們的裝置或瀏覽器上設定 Cookie，則選擇加入服務可讓您設定訪客的通訊協定。
seo-title: 選擇加入服務
title: 選擇加入服務
uuid: aebd72ad-4118-471b-9755-d08a72caa0fd
translation-type: tm+mt
source-git-commit: 4fbfefddcf36855f32f2a4047e19ef0b22fc508c

---


# 選擇加入服務{#opt-in-service}

如果您可以在使用者造訪網站時，在他們的裝置或瀏覽器上設定 Cookie，則選擇加入服務可讓您設定訪客的通訊協定。

選擇加入服務是 Experience Cloud ID (ECID) 服務的擴充功能，其設計可讓您控制 Experience Cloud 解決方案是否能在使用者同意前，在網頁上建立訪客的 Cookie，以及要使用哪個解決方案來執行。選擇加入服務也可讓您設定通訊協定，以便整合您的同意管理平台 (CMP) 和現有系統，融入更廣大的設計中。

透過使用選擇加入服務，您可指定訪客是否能選擇一次加入所有 Adobe 解決方案，或依序提出解決方案以要求各方案的權限。客戶完成並記錄核准程序後，您便可以從所有的 Adobe 解決方案擷取 CMP 訪客核准。

The Opt-in service is implemented and configured easily using [Adobe Experience Platform Launch](https://docs.adobelaunch.com/) with the [Opt-in extension](../../implementation-guides/opt-in-service/launch.md). 亦可使用 [DTM](../../implementation-guides/opt-in-service/optin-dtm.md) 進行實作和設定。

請參閱[設定選擇加入服務](../../implementation-guides/opt-in-service/getting-started.md)了解如何開始使用。

>[!NOTE]
>
>選擇加入服務可讓您設定系統以核准或拒絕是否只下載 Adobe Cookie。不提供收集使用者同意偏好設定的支援，也並非偏好設定的存放庫。

>[!IMPORTANT]
>
>本文件的內容不是法律建議，且用意並非要取代法律建議。設定選擇加入實作時，請向貴公司的法務部門諮詢同意與實務的相關建議。

## 所有 Experience Cloud 解決方案的選擇加入 {#section-053e6224505542cf961896f0ca869e52}

選擇加入服務是根據您自身需求，用來建立同意選擇加入工作流程的工具，可讓您設計在使用者或同意控制者給予同意之前和之後所使用的反應 (執行標籤) 工作流程。

選擇加入服務可讓您設定 Adobe 解決方案的同意管理作法，以達成下列目的:

* 指出在大部分情況下，同意收集要求是否適用於使用者。
* 指定哪個解決方案允許產生 Cookie。
* 為使用者未明確同意或拒絕類別的解決方案，套用預設偏好設定。
* 根據使用者同意設定的變更內容，觸發自訂回應，讓您可以保留或更新使用者設定。

您可以使用選擇加入服務設定網站，允許在使用者選擇前，讓部分 Cookie 載入預先同意。您可以為新客戶設定選擇加入服務，以便在使用者同意後或選項開放使用後載入 Cookie。您也可以從現有的同意管理平台儲存或擷取選擇加入同意，或僅將選擇加入權限儲存在 Cookie。

![](assets/Opt-in-approval.png)

Adobe 解決方案接著便可檢查標籤是否通過核准，然後訂閱變更內容，最後擷取所有的選擇加入客戶。選擇加入服務可讓您直接透過解決方案的 JavaScript 資料庫或 ECID (若已實作) 取得權限。
