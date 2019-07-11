---
description: 將選擇加入服務實作為 Experience Cloud 解決方案所用的單一參考點 (在選擇加入中以類別形式參照)，以判斷是否要在訪客裝置上建立 Cookie。
seo-description: 將選擇加入服務實作為 Experience Cloud 解決方案所用的單一參考點 (在選擇加入中以類別形式參照)，以判斷是否要在訪客裝置上建立 Cookie。
seo-title: 設定選擇加入服務
title: 設定選擇加入服務
uuid: f1c27139-cef2-4122-af12-c839cfc82e6e
translation-type: ht
source-git-commit: 7d0df419c4af7f8a58ffa56b1176bf638bc0045b

---


# 設定選擇加入服務{#setting-up-opt-in-service}

將選擇加入服務實作為 Experience Cloud 解決方案所用的單一參考點 (在選擇加入中以類別形式參照)，以判斷是否要在訪客裝置上建立 Cookie。

選擇加入服務是隨 Experience Cloud ID (ECID) 提供的 JavaScript 資料庫，且以 `adobe` 物件的形式存在於全域 `adobe.optIn` 物件的訪客 JS 中。安裝的選擇加入服務可讓您指定訪客是否可以選擇一次加入所有 Adobe 解決方案，或依序提出解決方案並要求各方案的權限。選擇加入服務的同意管理功能可讓您依照特定的隱私權需求，以各種設定來實作。

選擇加入服務可讓您指定訪客是否可以選擇一次加入所有 Adobe 解決方案，或依序提出解決方案並要求各方案的權限。客戶完成並記錄核准程序後，所有的 Adobe 解決方案便能擷取 CMP 訪客核准，並以相關的同意呼叫回應。

## 必要條件 {#section-c39246f45e514c8ea9fdbe6f7ffa3ad0}

1. ECID 4.0 版。

   [下載](https://github.com/Adobe-Marketing-Cloud/id-service/releases)最新版 ECID。

1. 支援的資料庫

   * ECID 4.0 版或更新版本
   * AppMeasurement 2.11 版或更新版本
   * DIL 9.0
   * AT.js 1.7.0 版
   * AT.js Launch 擴充功能 9.0 版
   * 若為 Analytics，需 App Measurement 2.11 以及擴充功能 1.6 版
   * 若為 Target，需擴充功能 0.9.1 版

1. 精通您將用於選擇加入的同意管理架構，並瞭解任何額外必備條件。

   <!--
   For IAB, see here for additional pre-reqs.
   -->

1. 貴公司的隱私權要求將依您選擇遵循 GDPR 規定的方式而定。瞭解貴公司隱私權團隊可接受以預先同意狀態使用的資料庫為何。

若採用 [Adobe Launch](https://docs.adobelaunch.com/)，請使用[選擇加入服務擴充功能](../../implementation-guides/opt-in-service/launch.md)來設定選擇加入服務。

## 選擇加入服務類別 {#section-9ab0492ab4414f0ca16dc08d3a905f47}

訪客的選擇加入偏好設定取決於 Adobe Experience Cloud 解決方案，每個解決方案都會以類別來表示。`adobe.OptInCategories` 物件會提供類別，舉例來說，系統會以 `adobe.OptInCategories` 參照 ECID 元件。`ECID`。以下為 `adobe.OptInCategories` 的定義:

選擇加入設定是按類別來維護，每個 Experience Cloud 解決方案都會以類別來表示。

```
adobe.OptInCategories = { 
    AAM: "aam", 
    TARGET: "target",  
    ANALYTICS: "aa", 
    ECID: "ecid", 
     
};
```

選擇加入服務可讓您按照網站上使用的各 Adobe 解決方案來設定訪客的權限偏好設定。選擇加入服務包含資料庫，可按核准的類別儲存訪客的設定，並支援序列流程，即核准程序一次會收到一個各類別的「確認」或「拒絕」偏好設定。您可以設定解決方案/類別，來選擇以全部或個別解決方案加入。所有 Adobe 解決方案的用戶端資料庫取決於選擇加入服務，除非解決方案已授予權限，否則其不會產生 Cookie。選擇加入支援多種方法，可提供並更新目前訪客的同意設定。本節提供設定選擇加入服務偏好設定的範例。請參閱[選擇加入 API 參考資料](../../implementation-guides/opt-in-service/api.md#reference-4f30152333dd4990ab10c1b8b82fc867)，以取得函數和參數的完整清單。

訪客 JS 的 `getInstance()` 函數中提供選擇加入服務設定，可實例化全域 `adobe` 物件。下表列出與選擇加入服務有關的訪客 JS [組態設定](../../implementation-guides/opt-in-service/api.md#section-d66018342baf401389f248bb381becbf)。

全域 **物件`Visitor`初始化中的選擇加入設定範例**

```
// FORMAT: Object<adobe.OptInCategories enum: boolean> 
var preOptInApprovalsConfig = {}; 
preOptInApprovals[adobe.OptInCategories.ANALYTICS] = true; 
  
// FORMAT: Object<adobe.OptInCategories enum: boolean> 
// If you are storing the OptIn permissions on your side (in a cookie you manage or in a CMP), 
// you have to provide those permissions through the previousPermissions config. 
// previousPermissions will overwrite preOptInApprovals. 
var previousPermissionsConfig = {}; 
previousPermissionsConfig[adobe.OptInCategories.AAM] = true; 
previousPermissionsConfig[adobe.OptInCategories.ANALYTICS] = false; 
  
Visitor.getInstance("YOUR_ORG_ID", { 
    "doesOptInApply": true, // NOTE: This can be a function that evaluates to true or false. 
    "preOptInApprovals": preOptInApprovalsConfig, 
    "previousPermissions": previousPermissionsConfig, 
    "isOptInStorageEnabled": true 
});
```

**處理同意的變更**

訪客在您的網站上體驗時，可能會隨時首次設定偏好設定，或使用您的 CMP 變更偏好設定。以初始設定初始化訪客 JS 後，訪客的權限就能變更。請參閱[同意的變更](../../implementation-guides/opt-in-service/api.md#section-c3d85403ff0d4394bd775c39f3d001fc)，以取得管理同意函數的清單。

<!--
<p> *** <b>sample code block </b>*** </p>
-->

## 選擇加入工作流程 {#section-70cd243dec834c8ea096488640ae20a5}

選擇加入服務支援可從多個要求週期收集權限的工作流程，且一次會指定一項偏好設定。使用下列函數並將 ** 設為 `shouldWaitForComplete`true，您的解決方案便能夠收集一個解決方案或全部類別之子集合的同意，然後收集下一個解決方案或類別子集合的同意。從首次呼叫開始，`adobe.optIn.status` 屬性會*擱置*，直到流程結束時呼叫 `adobe.optIn.complete()` 為止。呼叫後，狀態會設為 *complete*。

```
adobe.optIn.approve(['AAM', 'ECID'], true); 
adobe.optIn.deny(['ANALYTICS'], true); 
adobe.optIn.complete();
```

請參閱[工作流程組態設定](../../implementation-guides/opt-in-service/api.md#section-2c5adfa5459c4e72b96d2693123a53c2)。

## 檢查訪客的選擇加入權限 {#section-f136a9024e054d84881e6667fb7c94eb}

當訪客變更其權限時，您需深入掌握變更後的權限，以便同意對儲存區與選擇加入服務所做的變更進行同步。使用[權限函數](../../implementation-guides/opt-in-service/api.md#section-7fe57279b5b44b4f8fe47e336df60155)來檢查訪客的偏好設定，例如:

**fetchPermissions 範例**

```
optIn.fetchPermissions(function (permissions) { 
    // Here you can check if your category has been approved or not. 
    // We recommend using optIn.isApproved() to check for permissions because it abstracts out the details of knowing exactly how the permissions list looks like. 
    if (adobe.optIn.isApproved(MY_CATEGORY) { 
        sendBeacon(); // Or something 
    } 
});

OR: You can pass in shouldAutoSubscribe as true, your callback will be used to subscribe to all OptIn events going forward:

function callback() { 
    if (adobe.optIn.isApproved(MY_CATEGORY) { 
        sendBeacon(); // Or something 
    } 
}

optIn.fetchPermissions(callback, true);
```

如需此工具的其他相關資訊，請參閱[請參閱 API 文件](../../implementation-guides/opt-in-service/api.md#reference-4f30152333dd4990ab10c1b8b82fc867)以深入瞭解本文件提及的所有函數、屬性或設定。

## 儲存訪客偏好設定 {#section-ef2884ae67e34879bf7c7c3372706c9f}

選擇加入服務提供儲存同意偏好設定的選項，適合開發環境或無法使用 CRM 的環境使用。將設定屬性 `isOptInStorageEnabled` 指定為 *true*，便會觸發選擇加入服務在您的網域中於訪客的系統上建立 Cookie。

`adobe.optIn` 物件沒有狀態，不會提供儲存機制。這種設計的目的是，如果您現有的同意管理平台 (CMP) 允許儲存自訂資料，則您要在自己的平台上管理 Adobe 同意設定。或者，您可以將訪客偏好設定儲存在訪客瀏覽器上的 Cookie 中。您有兩個選項可以將使用者偏好設定提供給選擇加入服務:

* 如果您的同意持續性解決方案 (不論是 CMP 還是訪客瀏覽器上的 Cookie) 允許及時擷取訪客偏好設定，則您可以在訪客初始化期間提供這些偏好設定給選擇加入服務。
* 不過，如果擷取可能會是個耗時的流程，或是以非同步流程處理為最佳方式，您可以使用服務的 `approve()` 函數，在這些設定成功載入後用來提供這些設定。

