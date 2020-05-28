---
description: 連結同意管理平台 (CMP) 和選擇加入的適用於 IAB 透明與同意架構 (TCF) Audience Manager 增效模組。
seo-description: 連結同意管理平台 (CMP) 和適用於 IAB 透明與同意架構 (TCF) 的 Audience Manager 增效模組。
seo-title: 搭配 IAB 架構使用選擇加入服務
title: 搭配 IAB 架構使用選擇加入服務
uuid: 8df39d9c-c016-490e-b4db-d02e4044b480
translation-type: tm+mt
source-git-commit: bb61c33491cb67795d58575c5dca5fa2ba4c372f
workflow-type: tm+mt
source-wordcount: '502'
ht-degree: 65%

---


# 搭配 IAB 架構使用選擇加入服務{#using-opt-in-services-with-iab-framework}

連結同意管理平台 (CMP) 和選擇加入之適用於 IAB TCF 的 Audience Manager 增效模組。

使用 [IAB 透明與同意架構 (TCF)](https://iabtechlab.com/standards/gdpr-transparency-and-consent-framework/) 的 Audience Manager 客戶，可連結其同意管理平台 (CMP) 和選擇加入之適用於 IAB TCF 的 Audience Manager 增效模組。選擇加入是 ECID JavaScript 資料庫中內嵌的一項功能，視 CMP 中設定的訪客偏好設定而定，可停用個別 Adobe 解決方案資料庫。當IAB TCF的Audience Manager外掛程式與ECID程式庫一起實作時，您CMP中支援IAB TCF的訪客偏好設定會自動對應至選擇加入。 收到同意時，這些偏好設定會啟用以 Audience Manager 為基礎的資料庫 (DIL 與 ECID) 和相關聯的呼叫。

## 實作支援 IAB 的 CMP {#section-9fd2403b548947dbb1921ac6ff9d0c82}

為了讓選擇加入與IAB TCF整合，您必須完成下列工作：

1. Implement a CMP that supports IAB and is [registered as an IAB vendor](https://vendorlist.consensu.org/vendorlist.json) or develop an in-house CMP that implements the IAB TCF spec, and register as a CMP with IAB TCF.
1. 先定義/載入 `__cmp` 再載入 Adobe JS。

如需詳細資訊，請參閱[互動廣告局 (Interactive Advertising Bureau) 文件](https://github.com/InteractiveAdvertisingBureau/GDPR-Transparency-and-Consent-Framework/blob/master/v1.1%20Implementation%20Guidelines.md)。

## 在 ECID Javascript 資料庫啟用適用於 IAB TCF 的 Audience Manager 增效模組 {#section-77bf1b9ed67241a59e56c21ab752e82f}

>[!NOTE]
>
>只有ECID 4.0+才提供選擇加入。

使用 Adobe Experience Platform Launch 啟用您網站的選擇加入和適用於 IAB TCF 的 Audience Manager 增效模組。當您手動啟用選擇加入的 IAB 時，請檢查以確定在訪客物件中，下列設定皆設為 true：

```
Visitor.getInstance("YOUR_ORG_ID", {  
  doesOptInApply: true,   
  isIabContext: true   
});
```

在正確設定設定後，ECID和DIL程式庫將會根據來自CMP和IAB TCF的同意標準啟用／停用。

>[!IMPORTANT]
>
>Audience Manager needs consent for *Purpose 1 and Purpose 10, plus vendor consent* in order to deploy cookies and initiate or honor ID syncs. 若要深入了解有關適用於 IAB TCF 的 Audience Manager 增效模組，請參閱[這裡](https://docs.adobe.com/help/zh-Hant/audience-manager/user-guide/overview/gdpr/aam-iab-plugin.html)的 Audience Manager 文件。

如需如何驗證選擇加入和適用於 IAB TCF 的 Audience Manager 增效模組的詳細資訊，請在[這裡](../../implementation-guides/opt-in-service/testing-optin-and-iab-plugin.md#section-ca5c6f92fbdf4fd29b4acb6b644efbd0)參閱驗證指南中的使用案例 4。

## 相關文件 {#section-55da1110051a4b39b1037803f4a7b264}

* [IAB 透明與同意架構 (TCF)](https://iabtechlab.com/standards/gdpr-transparency-and-consent-framework/) - IAB 標準的詳細資訊
* [Adobe 選擇加入](../../implementation-guides/opt-in-service/optin-overview.md#concept-f9b5db0d27a245fbadd3e19162319360) - 選擇加入的詳細資訊；選擇加入為平台解決方案中同意管理的必要元件
* IAB Transparency and Consent Framework (TCF) Support [in Audience Manager](https://docs.adobe.com/content/help/zh-Hant/audience-manager/user-guide/overview/data-privacy/consent-management/aam-iab-plugin.html)
* [您的隱私權選擇](https://www.adobe.com/tw/privacy/opt-out.html#customeruse) -您的使用者可選擇的另一個隱私權選項，是使用其他全域選擇退出工具選擇退出所有資料收集。 全域退出優先於加入和IAB TCF驗證

