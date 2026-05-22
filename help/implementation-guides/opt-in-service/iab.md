---
description: 連結同意管理平台 (CMP) 和「選擇加入」適用於 IAB 的透明與同意架構 (TCF) Audience Manager 增效模組。
title: 搭配 IAB 架構使用「選擇加入」服務
exl-id: 9ac9b232-0797-4e77-a611-9cf5d17a5cb7
TQID: https://experienceleague.adobe.com/70QH1BoRSSbiw7cMfRjrHmiSxQLbuiHcWAG5b-xVOLw
product_v2: id: e1971122-7081-4556-9222-8a31bd71800c
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554id: c66ffd68-0f65-42bb-aa23-b4020f12e0bdid: f8a45b24-4be7-4f1b-909b-60d06b483a20id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2: id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87cid: d3cdead0-685a-4489-9250-4bb709942f66id: f4e6943a-c91a-4134-a2c7-f4f20cfff2f0
source-git-commit: 5c41e39a833b527a329f62e5f0929445f47139de
workflow-type: tm+mt
source-wordcount: 518
ht-degree: 96%

---

# 搭配 IAB 架構使用「選擇加入」服務{#using-opt-in-services-with-iab-framework}

>[!IMPORTANT]
>
>以下檔案僅適用於IAB 2.0。 使用者需使用Visitor.js version 5.0才能使用IAB 2.0。

將「同意管理平台」(CMP) 與「選擇加入」的 IAB 透明度與同意架構 (TCF) 外掛程式連線。

使用 [IAB TCF](https://iabtechlab.com/standards/gdpr-transparency-and-consent-framework/) 的 Adobe Audience Manager 客戶可將「同意管理平台」(CMP) 與「選擇加入」的 IAB TCF 外掛程式連線。 「選擇加入」是 ECID JavaScript 程式庫中嵌入的一項功能，視 CMP 中設定的訪客偏好設定而定，可停用個別 Adobe 解決方案程式庫。 使用 ECID 程式庫實作「選擇加入」的 IAB TCF 外掛程式時，支援 IAB TCF 之 CMP 的訪客偏好設定會自動對應到「選擇加入」。 收到同意時，這些偏好設定會啟用以 Audience Manager 為基礎的程式庫 (DIL 與 ECID) 和相關聯的呼叫。

## 實作支援 IAB 的 CMP {#section-9fd2403b548947dbb1921ac6ff9d0c82}

若要使「選擇加入」能與 IAB TCF 相互整合，您需完成下列操作：

1. 實作支援 IAB 且註冊為 IAB 廠商的 CMP，或開發會實作 IAB TCF 規格的內部 CMP，並註冊為具有 IAB TCF 的 CMP。
1. 先定義/載入 `__tcfapi` 再載入 Adobe JS。

如需詳細資訊，請參閱[互動廣告局 (Interactive Advertising Bureau) 文件](https://github.com/InteractiveAdvertisingBureau/GDPR-Transparency-and-Consent-Framework/blob/master/TCFv2/TCF-Implementation-Guidelines.md)。

## 在您的 ECID JavaScript 程式庫中啟用「選擇加入」的 IAB TCF 外掛程式 {#section-77bf1b9ed67241a59e56c21ab752e82f}

>[!NOTE]
>
>僅 ECID 4.0 (含) 以後版本提供「選擇加入」。

使用 Adobe Experience Platform Launch 為您的網站實作「選擇加入」的 IAB TCF 外掛程式。 手動啟用「選擇加入」的 IAB 時，請檢查以確定在訪客物件中，下列設定皆設為 true：

```javascript
Visitor.getInstance("YOUR_ORG_ID", {  
  doesOptInApply: true,
  isIabContext: true
});
```

設定正確設定後，ECID 和 DIL 程式庫就會根據 CMP 和 IAB TCF 的同意標準啟用/停用。

>[!IMPORTANT]
>
>Audience Manager 需要&#x200B;*目的 1 和 10 的同意，加上廠商同意*，才能部署 Cookie，並初始化或執行 ID 同步作業。 請到[此處](https://experienceleague.adobe.com/docs/audience-manager/user-guide/overview/data-privacy/consent-management/aam-iab-plugin.html?lang=zh-Hant)參閱 Audience Manager 文件中「選擇加入」之 IAB TCF 外掛程式的詳細資訊。

如需驗證「選擇加入」和 IAB TCF 外掛程式的詳細資訊，請到[此處](../../implementation-guides/opt-in-service/testing-optin-and-iab-plugin.md#section-ca5c6f92fbdf4fd29b4acb6b644efbd0)參閱驗證指南中的使用案例 4。

## 相關文件 {#section-55da1110051a4b39b1037803f4a7b264}

* [IAB 透明與同意架構 (TCF)](https://iabtechlab.com/standards/gdpr-transparency-and-consent-framework/) - IAB 標準的詳細資訊
* [Adobe 選擇加入](../../implementation-guides/opt-in-service/optin-overview.md#concept-f9b5db0d27a245fbadd3e19162319360) -「選擇加入」的詳細資訊；「選擇加入」是平台解決方案中同意管理的必要元件
* [Audience Manager](https://experienceleague.adobe.com/docs/audience-manager/user-guide/overview/data-privacy/consent-management/aam-iab-plugin.html?lang=zh-Hant) 中的 IAB 透明與同意架構 (TCF) 支援
* [您的隱私權選擇](https://www.adobe.com/tw/privacy/opt-out.html#customeruse) - 另一個可由用戶自行決定的隱私權選項，是使用其他全域選擇退出工具，選擇退出所有資料收集作業。 全域「選擇退出」的效力優先於「選擇加入」和 IAB 驗證

