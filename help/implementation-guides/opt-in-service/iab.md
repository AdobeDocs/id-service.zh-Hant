---
description: 將他們的同意管理平台(CMP)與選擇加入的IAB增效模組連結。
seo-description: 將他們的同意管理平台(CMP)與選擇加入的IAB增效模組連結。
seo-title: (測試版)搭配使用選擇加入服務與IAB Framework
title: (測試版)搭配使用選擇加入服務與IAB Framework
uuid: 8df39d9c-c016-490e-b4 db-d02 e4044 b480
translation-type: tm+mt
source-git-commit: bc5c81455023e22e64877bb861dfe141e158599c

---


# (測試版)搭配使用選擇加入服務與IAB Framework{#beta-using-opt-in-services-with-iab-framework}

將他們的同意管理平台(CMP)與選擇加入的IAB增效模組連結。

使用 [IAB透明度與同意框架(TCF)](https://iabtechlab.com/standards/gdpr-transparency-and-consent-framework/) 的Audience Manager客戶可將其同意管理平台(CMP)與選擇加入的IAB增效模組連接。選擇加入是內嵌於ECID JavaScript程式庫中的功能，可根據在CMP中設定的訪客偏好設定，停用個別的Adobe解決方案程式庫。當IAB增效模組使用ECID程式庫實施時，您的IAB相容CMP的訪客偏好設定會自動對應至選擇加入。這些偏好設定將在收到同意時啓用Audience Manager庫(DIL和ECID)和相關呼叫。

## 實作支援 IAB 的 CMP {#section-9fd2403b548947dbb1921ac6ff9d0c82}

為了讓選擇加入能與 IAB 同意整合，您需要完成下列操作:

1. 實作支援 IAB 且[註冊為 IAB 廠商](https://vendorlist.consensu.org/vendorlist.json)的 CMP，或開發會實作 IAB 規格的內部 CMP，並註冊為具有 IAB Europe 的 CMP。
1. 在載入Adobe JS `__cmp` 之前定義/載入。

如需詳細資訊，請參閱[互動廣告局 (Interactive Advertising Bureau) 文件](https://github.com/InteractiveAdvertisingBureau/GDPR-Transparency-and-Consent-Framework/blob/master/v1.1%20Implementation%20Guidelines.md)。

## 在您的 ECID JavaScript 資料庫中啟用 IAB 增效模組 {#section-77bf1b9ed67241a59e56c21ab752e82f}

>[!NOTE]
>
>選擇加入只能在EID4.0+中使用

使用 Adobe Launch 來啟用您網站的選擇加入和 IAB 增效模組。請參閱 [ECID 選擇加入擴充功能文件](https://marketing-beta.adobe.com/resources/help/launch/ecid-optin/)，瞭解如何設定 Launch 擴充功能。

當您手動啟用選擇加入的 IAB 時，請檢查以確定在訪客物件中，下列設定皆設為 true:

```
Visitor.getInstance("YOUR_ORG_ID", {  
  doesOptInApply: true,   
  isIabContext: true   
});
```

妥善設定後，ECID 和 DIL 資料庫便會視 CMP 和 IAB 架構的同意條件來啟用/停用。

>[!IMPORTANT]
>
>Audience Manager 需要*目的 1、2 和 5 的同意，加上廠商同意*，才能部署 Cookie，並初始化或執行 ID 同步。請參閱AAB plugin in Audience Manager文件** [此處](https://marketing-beta.adobe.com/resources/help/aam/iab-support/aam-iab-support.html)**。

如需如何驗證選擇加入和 IAB 增效模組的詳細資訊，請[**在此**](../../implementation-guides/opt-in-service/testing-optin-and-iab-plugin.md#section-ca5c6f92fbdf4fd29b4acb6b644efbd0)參閱驗證指南中的使用案例 4。

## 相關文件 {#section-55da1110051a4b39b1037803f4a7b264}

* [IAB 透明與同意架構 (TCF)](https://iabtechlab.com/standards/gdpr-transparency-and-consent-framework/) - 如需 IAB 標準的詳細資訊
* [Adobe 選擇加入](../../implementation-guides/opt-in-service/optin-overview.md#concept-f9b5db0d27a245fbadd3e19162319360) - 如需選擇加入的詳細資訊；選擇加入為平台解決方案中同意管理的必要元件
* [Audience Manager 中的](https://marketing-beta.adobe.com/resources/help/aam/iab-support/aam-iab-support.html) IAB 透明與同意架構 (TCF) 支援
* [您的隱私權選擇](https://www.adobe.com/privacy/opt-out.html#customeruse) - 另一個可由使用者自行決定的隱私權選項是，是可使用其他全域選擇退出工具來選擇退出所有資料收集。全域選擇退出優先於選擇加入和 IAB 驗證

