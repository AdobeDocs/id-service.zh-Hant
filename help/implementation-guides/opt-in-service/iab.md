---
description: 連結同意管理平台 (CMP) 和「選擇加入」適用於 IAB 的透明與同意架構 (TCF) Audience Manager 外掛程式。
seo-description: 連結同意管理平台 (CMP) 和適用於 IAB 透明與同意架構 (TCF) 的 Audience Manager 外掛程式。
seo-title: 搭配 IAB 架構使用「選擇加入」服務
title: 搭配 IAB 架構使用「選擇加入」服務
uuid: 8df39d9c-c016-490e-b4db-d02e4044b480
translation-type: tm+mt
source-git-commit: ddff95876722b981f22c7e3196ff2ce9b696010e
workflow-type: tm+mt
source-wordcount: '493'
ht-degree: 100%

---


# 搭配 IAB 架構使用「選擇加入」服務{#using-opt-in-services-with-iab-framework}

>[!IMPORTANT]
>
> 以下文件僅適用於 IAB 2.0。使用者需使用 Visitor.js version 5.0 才能使用 IAB 2.0。

將「同意管理平台」(CMP) 與「選擇加入」的 IAB 透明度與同意架構 (TCF) 外掛程式連線。

使用 [IAB TCF](https://iabtechlab.com/standards/gdpr-transparency-and-consent-framework/) 的 Adobe Audience Manager 客戶可將「同意管理平台」(CMP) 與「選擇加入」的 IAB TCF 外掛程式連線。「選擇加入」是 ECID JavaScript 資料庫中內嵌的一項功能，視 CMP 中設定的訪客偏好設定而定，可停用個別 Adobe 解決方案資料庫。使用 ECID 資料庫實作「選擇加入」的 IAB TCF 外掛程式時，支援 IAB TCF 之 CMP 的訪客偏好設定會自動對應到「選擇加入」。收到同意時，這些偏好設定會啟用以 Audience Manager 為基礎的資料庫 (DIL 與 ECID) 和相關聯的呼叫。

## 實作支援 IAB 的 CMP {#section-9fd2403b548947dbb1921ac6ff9d0c82}

若要使「選擇加入」能與 IAB TCF 相互整合，您需完成下列操作：

1. 實作支援 IAB 且[註冊為 IAB 廠商](https://vendorlist.consensu.org/vendorlist.json)的 CMP，或開發會實作 IAB TCF 規格的內部 CMP，並註冊為具有 IAB TCF 的 CMP。
1. 先定義/載入 `__tcfapi` 再載入 Adobe JS。

如需詳細資訊，請參閱[互動廣告局 (Interactive Advertising Bureau) 文件](https://github.com/InteractiveAdvertisingBureau/GDPR-Transparency-and-Consent-Framework/blob/master/TCFv2/TCF-Implementation-Guidelines.md)。

## 在您的 ECID JavaScript 資料庫中啟用「選擇加入」的 IAB TCF 外掛程式 {#section-77bf1b9ed67241a59e56c21ab752e82f}

>[!NOTE]
>
>僅 ECID 4.0 (含) 以後版本提供「選擇加入」。

使用 Adobe Experience Platform Launch 為您的網站實作「選擇加入」的 IAB TCF 外掛程式。手動啟用「選擇加入」的 IAB 時，請檢查以確定在訪客物件中，下列設定皆設為 true：

```javascript
Visitor.getInstance("YOUR_ORG_ID", {  
  doesOptInApply: true,
  isIabContext: true
});
```

設定正確設定後，ECID 和 DIL 資料庫就會根據 CMP 和 IAB TCF 的同意標準啟用/停用。

>[!IMPORTANT]
>
>Audience Manager 需要&#x200B;*目的 1 和 10 的同意，加上廠商同意*，才能部署 Cookie，並初始化或執行 ID 同步作業。請到[此處](https://docs.adobe.com/help/zh-Hant/audience-manager/user-guide/overview/gdpr/aam-iab-plugin.html)參閱 Audience Manager 文件中「選擇加入」之 IAB TCF 外掛程式的詳細資訊。

如需驗證「選擇加入」和 IAB TCF 外掛程式的詳細資訊，請到[此處](../../implementation-guides/opt-in-service/testing-optin-and-iab-plugin.md#section-ca5c6f92fbdf4fd29b4acb6b644efbd0)參閱驗證指南中的使用案例 4。

## 相關文件 {#section-55da1110051a4b39b1037803f4a7b264}

* [IAB 透明與同意架構 (TCF)](https://iabtechlab.com/standards/gdpr-transparency-and-consent-framework/) - IAB 標準的詳細資訊
* [Adobe 選擇加入](../../implementation-guides/opt-in-service/optin-overview.md#concept-f9b5db0d27a245fbadd3e19162319360) -「選擇加入」的詳細資訊；「選擇加入」是平台解決方案中同意管理的必要元件
* [Audience Manager](https://docs.adobe.com/content/help/zh-Hant/audience-manager/user-guide/overview/data-privacy/consent-management/aam-iab-plugin.html) 中的 IAB 透明與同意架構 (TCF) 支援
* [您的隱私權選擇](https://www.adobe.com/tw/privacy/opt-out.html#customeruse) - 另一個可由使用者自行決定的隱私權選項，是使用其他全域選擇退出工具，選擇退出所有資料收集作業。全域「選擇退出」的效力優先於「選擇加入」和 IAB 驗證