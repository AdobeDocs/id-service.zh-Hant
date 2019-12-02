---
description: 連結同意管理平台 (CMP) 和選擇加入的適用於 IAB 透明與同意架構 (TCF) Audience Manager 增效模組。
seo-description: 連結同意管理平台 (CMP) 和適用於 IAB 透明與同意架構 (TCF) 的 Audience Manager 增效模組。
seo-title: (測試版) 搭配 IAB 架構使用選擇加入服務
title: (測試版) 搭配 IAB 架構使用選擇加入服務
uuid: 8df39d9c-c016-490e-b4db-d02e4044b480
translation-type: tm+mt
source-git-commit: 27d3da940e4bba20a4eba86edfc44bf834173d6a

---


# (測試版) 搭配 IAB 架構使用選擇加入服務{#beta-using-opt-in-services-with-iab-framework}

將其同意管理平台(CMP)與Opt-in的Audience Manager IAB外掛程式(for Audience Manager)連結。

使用 [IAB 透明與同意架構 (TCF)](https://iabtechlab.com/standards/gdpr-transparency-and-consent-framework/) 的 Audience Manager 客戶，可連結其同意管理平台 (CMP) 和選擇加入之適用於 IAB TCF 的 Audience Manager 增效模組。選擇加入是 ECID JavaScript 資料庫中內嵌的一項功能，視 CMP 中設定的訪客偏好設定而定，可停用個別 Adobe 解決方案資料庫。當IAB TCF的Audience manager外掛程式與ECID程式庫一起實作時，您符合IAB的CMP的訪客偏好設定會自動對應至選擇加入。 收到同意時，這些偏好設定會啟用以 Audience Manager 為基礎的資料庫 (DIL 與 ECID) 和相關聯的呼叫。

## 實作支援 IAB 的 CMP {#section-9fd2403b548947dbb1921ac6ff9d0c82}

為了讓選擇加入能與 IAB 同意整合，您需要完成下列操作：

1. 實作支援 IAB 且[註冊為 IAB 廠商](https://vendorlist.consensu.org/vendorlist.json)的 CMP，或是開發會實作 IAB 規格的內部 CMP，並註冊為具有 IAB Europe 的 CMP。
1. 先定義/載入 `__cmp` 再載入 Adobe JS。

如需詳細資訊，請參閱[互動廣告局 (Interactive Advertising Bureau) 文件](https://github.com/InteractiveAdvertisingBureau/GDPR-Transparency-and-Consent-Framework/blob/master/v1.1%20Implementation%20Guidelines.md)。

## 在您的ECID Javascript程式庫中啟用IAB的Audience Manager外掛程式 {#section-77bf1b9ed67241a59e56c21ab752e82f}

>[!NOTE]
>
>僅 ECID 4.0 或更新版本提供選擇加入

使用Adobe Experience Platform Launch，為您的網站實作IAB TCF的Opt-in和Audience manager外掛程式。 當您手動啟用選擇加入的 IAB 時，請檢查以確定在訪客物件中，下列設定皆設為 true：

```
Visitor.getInstance("YOUR_ORG_ID", {  
  doesOptInApply: true,   
  isIabContext: true   
});
```

妥善設定後，ECID 和 DIL 資料庫便會視 CMP 和 IAB 架構的同意條件來啟用/停用。

>[!IMPORTANT]
>
>Audience Manager 需要&#x200B;*目的 1、2 和 5 的同意，加上廠商同意*，才能部署 Cookie，並初始化或執行 ID 同步。請[在此](https://docs.adobe.com/help/en/audience-manager/user-guide/overview/gdpr/aam-iab-plugin.html)參閱 Audience Manager 文件中 IAB 增效模組的詳細資訊。

For more information on how to validate both Opt-in and the Audience Manager plug-in for IAB, check use case #4 in the validation guide [here](../../implementation-guides/opt-in-service/testing-optin-and-iab-plugin.md#section-ca5c6f92fbdf4fd29b4acb6b644efbd0).

## 相關文件 {#section-55da1110051a4b39b1037803f4a7b264}

* [IAB 透明與同意架構 (TCF)](https://iabtechlab.com/standards/gdpr-transparency-and-consent-framework/) - IAB 標準的詳細資訊
* [Adobe 選擇加入](../../implementation-guides/opt-in-service/optin-overview.md#concept-f9b5db0d27a245fbadd3e19162319360) - 選擇加入的詳細資訊；選擇加入為平台解決方案中同意管理的必要元件
* [Audience Manager 中的](https://marketing-beta.adobe.com/resources/help/aam/iab-support/aam-iab-support.html) IAB 透明與同意架構 (TCF) 支援
* [您的隱私權選擇](https://www.adobe.com/privacy/opt-out.html#customeruse) - 另一個可由使用者自行決定的隱私權選項是，是可使用其他全域選擇退出工具來選擇退出所有資料收集。全域選擇退出優先於選擇加入和 IAB 驗證

